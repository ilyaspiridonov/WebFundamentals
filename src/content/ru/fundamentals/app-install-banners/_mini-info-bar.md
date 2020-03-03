## The mini-info bar {: #mini-info-bar }

<figure class="attempt-right">   <img class="screenshot" src="/web/updates/images/2018/06/a2hs-infobar-cropped.png">   <figcaption>     The mini-infobar   </figcaption> </figure>

**Мини-информационная панель - это промежуточный опыт для Chrome на Android,** поскольку мы работаем над созданием согласованного интерфейса для всех платформ, который включает кнопку установки в омнибоксе.

The mini-infobar is a Chrome UI component and is not controllable by the site, but can be easily dismissed by the user. Once dismissed by the user, it will not appear again until a sufficient amount of time has passed (currently 3 months). The mini-infobar will appear when the site meets the [criteria](#criteria), regardless of whether you `preventDefault()` on the `beforeinstallprompt` event or not.

Примечание. Мини-информационная панель не отображается на настольных устройствах.
