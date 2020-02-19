project_path: /web/fundamentals/_project.yaml book_path: /web/fundamentals/_book.yaml описание: собственные баннеры установки приложений позволяют пользователям быстро и без проблем устанавливать родное приложение на свое устройство из магазина приложений, не выходя из магазина приложений. браузер.

{# wf_updated_on: 2019-02-08 #} {# wf_published_on: 2014-12-16 #} {# wf_blink_components: платформа> Приложения> AppLauncher> Install #}

# Запрос установки собственного приложения {: .page-title}

The native app install prompt gives you the ability to let users quickly and seamlessly install your native app on their device directly from the app store, without leaving the browser, and without showing an annoying interstitial.

## Каковы критерии? {: # критерии}

Чтобы отобразить пользователю приглашение на установку собственного приложения, ваш сайт должен соответствовать следующим критериям:

- Веб-приложение и нативное приложение уже установлены.
- Соответствует эвристике взаимодействия с пользователем (в настоящее время пользователь взаимодействует с доменом не менее 30 секунд)
- Включает [манифест веб-приложения,](/web/fundamentals/web-app-manifest/) который включает в себя:
    -  `short_name`
    -  `name` (используется в приглашении баннера)
    -  `icons` включая версию 192px и 512px
    -  [`prefer_related_applications`](#prefer_related) это `true`
    -  объект [`related_applications`](#prefer_related) с информацией о приложении
- Подается по **HTTPS**

Когда эти критерии будут выполнены, будет `beforeinstallprompt` событие `beforeinstallprompt` которое вы можете использовать, чтобы предложить пользователю установить ваше собственное приложение, и может отобразиться [мини-информационная панель](#mini-info-bar) .

### Обязательные свойства манифеста {: #prefer_related}

Чтобы предложить пользователю установить ваше собственное приложение, вам нужно добавить два свойства в манифест веб-приложения: `prefer_related_applications` и `related_applications` .

```
"prefer_related_applications": true,
"related_applications": [
  {
    "platform": "play",
    "id": "com.google.samples.apps.iosched"
  }
]
```

### `prefer_related_applications` {: #prefer_related_applications}

Свойство `prefer_related_applications` указывает браузеру запрашивать у пользователя собственное приложение вместо веб-приложения. Если это значение не задано или равно `false` , браузер предложит пользователю установить веб-приложение.

### `related_applications` {: #related_applications}

`related_applications` - это массив со списком объектов, которые сообщают браузеру о предпочитаемом вами родном приложении. Каждый объект должен включать свойство `platform` свойство `id` . Где `play` `platform` а `id` - это `id` приложения Play Store.

## Показать приглашение установки {: #trigger}

Чтобы отобразить диалог установки, вам необходимо:

1. Прослушайте событие `beforeinstallprompt`
2. Уведомите пользователя, что ваше родное приложение может быть установлено с помощью кнопки или другого элемента, который сгенерирует событие жеста пользователя.
3. Показать приглашение, вызвав `prompt()` для сохраненного события `beforeinstallprompt` .

### Слушайте перед `beforeinstallprompt`

Если [критерии](#criteria) выполнены, Chrome `beforeinstallprompt` событие `beforeinstallprompt` , которое вы можете использовать, чтобы указать, что ваше приложение может быть установлено, а затем предложит пользователю установить его.

Когда событие `beforeinstallprompt` , сохраните ссылку на событие и обновите свой пользовательский интерфейс, чтобы указать, что пользователь может установить ваше приложение.

```js
let deferredPrompt;

window.addEventListener('beforeinstallprompt', (e) => {
  // Prevent Chrome 67 and earlier from automatically showing the prompt
  e.preventDefault();
  // Stash the event so it can be triggered later.
  deferredPrompt = e;
});
```

### Сообщите пользователю, что ваше приложение может быть установлено

Лучший способ уведомить пользователя о том, что ваше приложение может быть установлено, - добавить кнопку или другой элемент в ваш пользовательский интерфейс. **Не показывайте вставку всей страницы или другие элементы, которые могут раздражать или отвлекать.**

<pre class="prettyprint">window.addEventListener ('beforeinstallprompt', (e) => {// Предотвращение автоматического отображения приглашения Chrome 67 и более ранних версий e.preventDefault (); // Сохранение события, чтобы его можно было запустить позже. deferredPrompt = e; <strong>// Обновление пользовательского интерфейса уведомляет пользователя, которого он может добавить на домашний экран btnAdd.style.display = 'block';</strong> });</pre>

Успех: вы можете подождать, прежде чем показывать подсказку пользователю, чтобы не отвлекать их от того, что они делают. Например, если пользователь находится в процессе извлечения или создает свою учетную запись, дайте ему завершить это, прежде чем прерывать его с приглашением.

### Показать подсказку

Чтобы показать приглашение установки, вызовите `prompt()` для сохраненного события изнутри пользовательского жеста. Появится модальное диалоговое окно с просьбой добавить приложение на домашний экран.

Затем прослушайте обещание, возвращаемое свойством `userChoice` . Обещание возвращает объект с `outcome` свойством после того, как приглашение было показано, и пользователь ответил на него.

```js
btnAdd.addEventListener('click', (e) => {
  // hide our user interface that shows our A2HS button
  btnAdd.style.display = 'none';
  // Show the prompt
  deferredPrompt.prompt();
  // Wait for the user to respond to the prompt
  deferredPrompt.userChoice
    .then((choiceResult) => {
      if (choiceResult.outcome === 'accepted') {
        console.log('User accepted the A2HS prompt');
      } else {
        console.log('User dismissed the A2HS prompt');
      }
      deferredPrompt = null;
    });
});
```

Вы можете только вызвать `prompt()` для отложенного события один раз. Если пользователь отклонит его, вам нужно будет подождать, пока на следующей странице навигации не `beforeinstallprompt` событие `beforeinstallprompt` .

<< _ mini-info-bar.md >>

## Особые замечания при использовании политики безопасности контента

Если на вашем сайте действует ограничительная [политика безопасности контента](/web/fundamentals/security/csp/) , обязательно добавьте `*.googleusercontent.com` в директиву `img-src` чтобы Chrome мог загрузить значок, связанный с вашим приложением, из Play Store.

В некоторых случаях `*.googleusercontent.com` может быть более подробным, чем хотелось бы. Это можно сузить путем [удаленной отладки](/web/tools/chrome-devtools/remote-debugging/) устройства Android, чтобы определить URL-адрес значка приложения.

## Обратная связь {: .hide-from-toc}

{% include "web / _shared / полезно.html"%}

<div class="clearfix"></div>
