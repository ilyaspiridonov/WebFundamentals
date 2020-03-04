project_path: /web/fundamentals/_project.yaml book_path: /web/fundamentals/_book.yaml description: Ajouter à l'écran d'accueil vous permet de permettre aux utilisateurs d'ajouter rapidement et en toute transparence votre application Web à leurs écrans d'accueil sans quitter le navigateur.

{# wf_updated_on: 2019-03-19 #} {# wf_published_on: 2014-12-16 #} {# wf_blink_components: Platform> Apps> AppLauncher> Install #}

# Ajouter à l'écran d'accueil {: .page-title}

{% incluent "web / _shared / contributors / petelepage.html"%}

**Ajouter à l'écran d'accueil** , parfois appelé invite d'installation de l'application Web, permet aux utilisateurs d'installer facilement votre application Web progressive sur leur appareil mobile ou de [bureau](/web/progressive-web-apps/desktop) . Une fois que l'utilisateur a accepté l'invite, votre PWA sera ajouté à son lanceur et il fonctionnera comme n'importe quelle autre application installée.

Chrome gère la plupart des tâches lourdes pour vous:

- Sur mobile, Chrome générera un [WebAPK](/web/fundamentals/integration/webapks) , créant une expérience encore plus intégrée pour vos utilisateurs.
- Sur le bureau, votre application sera installée et exécutée dans une [fenêtre d'application](/web/progressive-web-apps/desktop#app-window) .

## Quels sont les critères? {: #Critères }

{% incluent "web / principes de base / bannières d'installation d'applications / _a2hs-critères.html"%}

Remarque: Si le manifeste de l'application Web inclut <code>related_applications</code> et a <code>"prefer_related_applications": true</code> , l' <a href="/web/fundamentals/app-install-banners/native">invite d'installation de l'application native</a> sera affichée à la place.

## Afficher la boîte de dialogue Ajouter à l'écran d'accueil {: #trigger}

<figure class="attempt-right"><img src="../../../en/fundamentals/app-install-banners/images/a2hs-dialog-g.png" alt="Boîte de dialogue Ajouter à l'écran d'accueil sur Android"><figcaption> Boîte de dialogue Ajouter à l'écran d'accueil sur Android </figcaption></figure>

Pour afficher la boîte de dialogue Ajouter à l'écran d'accueil, vous devez:

1. Écoutez l'événement `beforeinstallprompt`
2. Avertissez l'utilisateur que votre application peut être installée avec un bouton ou un autre élément qui générera un événement de geste utilisateur.
3. Affichez l'invite en appelant `prompt()` sur l'événement `beforeinstallprompt` enregistré.

<div class="clearfix"></div>

Remarque: Chrome 67 et versions antérieures affichaient une bannière "Ajouter à l'écran d'accueil". Il a été supprimé dans Chrome 68.

### Écoutez `beforeinstallprompt`

Si les [critères d'](#criteria) ajout à l'écran d'accueil sont remplis, Chrome déclenche un événement `beforeinstallprompt` , que vous pouvez utiliser pour indiquer que votre application peut être `` installée '', puis invite l'utilisateur à l'installer.

Une fois l'événement `beforeinstallprompt` déclenché, enregistrez une référence à l'événement et mettez à jour votre interface utilisateur pour indiquer que l'utilisateur peut ajouter votre application à son écran d'accueil.

```
let deferredPrompt;

window.addEventListener('beforeinstallprompt', (e) => {
  // Prevent Chrome 67 and earlier from automatically showing the prompt
  e.preventDefault();
  // Stash the event so it can be triggered later.
  deferredPrompt = e;
});
```

### Avertissez l'utilisateur que votre application peut être installée

La meilleure façon d'informer l'utilisateur de l'installation de votre application consiste à ajouter un bouton ou un autre élément à votre interface utilisateur. **Ne montrez pas une page entière interstitielle ou d'autres éléments qui peuvent être ennuyeux ou distrayants.**

<pre class="prettyprint">window.addEventListener ('beforeinstallprompt', (e) => {// Empêche Chrome 67 et versions antérieures d'afficher automatiquement l'invite e.preventDefault (); // Stash l'événement afin qu'il puisse être déclenché plus tard. deferredPrompt = e; <strong>// L'UI de mise à jour informe l'utilisateur qu'il peut l'ajouter à l'écran d'accueil btnAdd.style.display = 'block';</strong> });</pre>

Succès: vous voudrez peut-être attendre avant d'afficher l'invite à l'utilisateur, afin de ne pas le distraire de ce qu'il fait. Par exemple, si l'utilisateur est dans un flux de paiement ou crée son compte, laissez-le terminer avant de l'interrompre avec l'invite.

### Afficher l'invite

Pour afficher l'invite d'ajout à l'écran d'accueil, appelez `prompt()` sur l'événement enregistré à partir d'un geste utilisateur. Il affichera une boîte de dialogue modale, demandant à l'utilisateur d'ajouter votre application à son écran d'accueil.

Ensuite, écoutez la promesse retournée par la propriété `userChoice` . La promesse renvoie un objet avec une propriété de `outcome` une fois l'invite affichée et l'utilisateur y ayant répondu.

```
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

Vous ne pouvez appeler une fois `prompt()` sur l'événement différé. Si l'utilisateur le rejette, vous devrez attendre que l'événement `beforeinstallprompt` se déclenche sur la navigation de la page suivante.

<< _ mini-info-bar.md >>

## Commentaires {: .hide-from-toc}

{% incluent "web / _shared / utile.html"%}

<div class="clearfix"></div>

## Déterminez si l'application a été installée avec succès {: #appinstalled}

Pour déterminer si l'application a été ajoutée avec succès à l'écran d'accueil de l'utilisateur *après* avoir accepté l'invite, vous pouvez écouter l'événement `appinstalled` par l'application.

```
window.addEventListener('appinstalled', (evt) => {
  app.logEvent('a2hs', 'installed');
});
```

## Détecter si votre application est lancée à partir de l'écran d'accueil {: # detect-mode}

### requête média en `display-mode`

La requête multimédia en `display-mode` permet d'appliquer des styles en fonction de la façon dont l'application a été lancée ou de déterminer comment elle a été lancée avec JavaScript.

Pour appliquer une couleur d'arrière-plan différente pour l'application ci-dessus lors du lancement à partir de l'écran d'accueil avec `"display": "standalone"` , utilisez le CSS conditionnel:

```
@media all and (display-mode: standalone) {
  body {
    background-color: yellow;
  }
}
```

Il est également possible de détecter si le `display-mode` est autonome à partir de JavaScript:

```
if (window.matchMedia('(display-mode: standalone)').matches) {
  console.log('display-mode is standalone');
}
```

### Safari

Pour déterminer si l'application a été lancée en mode `standalone` dans Safari, vous pouvez utiliser JavaScript pour vérifier:

```
if (window.navigator.standalone === true) {
  console.log('display-mode is standalone');
}
```

## Mettre à jour l'icône et le nom de votre application

### Android

Sur Android, lorsque WebAPK est lancé, Chrome vérifie le manifeste actuellement installé par rapport au manifeste en direct. Si une mise à jour est requise, elle sera mise en [file d'attente et mise](/web/fundamentals/integration/webapks#update-webapk) à [jour](/web/fundamentals/integration/webapks#update-webapk) une fois que l'appareil est branché et connecté au WiFi.

### Bureau

Sur le bureau, le manifeste n'est pas automatiquement mis à jour, mais cela est prévu pour une future mise à jour.

## Testez votre expérience d'ajout à l'écran d'accueil {: #test}

Vous pouvez déclencher manuellement l'événement `beforeinstallprompt` avec Chrome DevTools. Cela permet de voir l'expérience utilisateur, de comprendre le fonctionnement du flux ou de déboguer le flux. Si les [critères PWA](#pwa-criteria) ne sont pas remplis, Chrome lèvera une exception dans la console et l'événement ne sera pas déclenché.

Attention: Chrome a un flux d'installation légèrement différent pour le bureau et le mobile. Bien que les instructions soient similaires, les tests sur mobile <b>nécessitent</b> un débogage à distance; sans cela, Chrome utilisera le flux d'installation du bureau.

### Chrome pour Android

1. Ouvrez une session de [débogage à distance](/web/tools/chrome-devtools/remote-debugging/) sur votre téléphone ou votre tablette.
2. Accédez au panneau **Application** .
3. Accédez à l'onglet **Manifest** .
4. Cliquez sur **Ajouter à l'écran d'accueil**

### Chrome OS, Linux ou Windows

1. Ouvrez Chrome DevTools
2. Accédez au panneau **Application** .
3. Accédez à l'onglet **Manifest** .
4. Cliquez sur **Ajouter à l'écran d'accueil**

### Est-ce que `beforeinstallprompt` sera déclenché?

The easiest way to test if the `beforeinstallprompt` event will be fired, is to use [Lighthouse](/web/tools/lighthouse/) to audit your app, and check the results of the [User Can Be Prompted To Install The Web App](/web/tools/lighthouse/audits/install-prompt) test.
