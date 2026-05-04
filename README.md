# Altekk VPN — Releases

Téléchargez l'APK depuis l'onglet [Releases](../../releases).

## Annonce in-app (banner sur l'écran principal de l'app)

Le `version.json` peut contenir un objet `announcement` optionnel pour afficher un banner orange dans l'app Android (au-dessus du bouton VPN). Format :

```json
{
  "announcement": {
    "id": "maintenance-2026-05-05",
    "expiresAt": "2026-05-05T23:00:00Z",
    "body": {
      "fr": "Le 5 mai 2026, mise à jour du serveur. Des perturbations sont possibles.",
      "ru": "5 мая 2026 г. — обновление сервера. Возможны временные перебои.",
      "en": "On May 5, 2026, server maintenance. Brief disruptions possible."
    }
  }
}
```

- `id` : identifiant stable. Si un user tape « Fermer », l'app retient l'id localement et ne réaffiche pas. Pour forcer un re-show, publier un id différent.
- `expiresAt` (UTC, ISO 8601) : facultatif. L'annonce disparaît automatiquement après cette date.
- `body` : multi-langue (fallback `en`).

**Pour pousser une annonce** : éditer `version.json`, ajouter le bloc `announcement`, `git push`. Le banner apparaît au prochain cold start de chaque app.

**Pour retirer** : supprimer le bloc `announcement` du JSON et push.
