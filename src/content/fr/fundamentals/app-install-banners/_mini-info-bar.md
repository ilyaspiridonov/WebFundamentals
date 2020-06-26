## La mini-barre d'informations {: # mini-info-bar}

<figure class="attempt-right"><img class="screenshot" src="/web/updates/images/2018/06/a2hs-infobar-cropped.png"><figcaption> Le mini-infobar </figcaption></figure>

**La mini-infobar est une expérience intermédiaire pour Chrome sur Android alors** que nous nous efforçons de créer une expérience cohérente sur toutes les plates-formes qui comprend un bouton d'installation dans l'omnibox.

La mini-barre d'informations est un composant de l'interface utilisateur de Chrome et n'est pas contrôlable par le site, mais peut être facilement ignorée par l'utilisateur. Une fois rejeté par l'utilisateur, il n'apparaîtra plus jusqu'à ce qu'un délai suffisant se soit écoulé (actuellement 3 mois). La mini-infobar apparaîtra lorsque le site répond aux [critères](#criteria) , que vous `preventDefault()` lors de l'événement `beforeinstallprompt` ou non.

Remarque: la mini-barre d'informations ne s'affiche pas sur les appareils de bureau.
