# DocPocket Suite - Console Centrale de Licences (PWA)

Tableau de bord unifié et autonome sous forme de **Progressive Web App (PWA)** permettant de superviser, générer et synchroniser les licences pour l'ensemble des applications de la suite DocPocket.

---

## 🚀 Fonctionnalités Clés

1. **🔒 Protection Administrateur par Code PIN :**
   - Code PIN initial : **`1980`** (modifiable à tout moment dans l'onglet Paramètres ⚙️).
   - Clavier virtuel numérique tactile + écoute native du clavier physique.
   - Verrouillage automatique configurable après 15 minutes d'inactivité.
   - Bouton de verrouillage instantané dans l'en-tête.

2. **📱 8 Applications Médicales & Professionnelles Réunies :**
   - **DocPocket Cabinet** : Nom, Prénom, N° Ordre, Spécialité, Ville, Téléphone, Postes (1 à 10), Validité (1 an, 2 ans, À vie). Clé format : `DPCAB-XX-YYYYMMDD-XXXX-XXXX`.
   - **DocPocket Medoc** : Nom, Prénom, N° d'Ordre. Clé déterministe SHA-256 avec sel `DOCPOCKET_MEDOCS_TUNISIE_2026_SECURE_SALT`. Format : `DOC-XXXX-XXXX-XXXX-XXXX`.
   - **DocPocket SMS RDV** : Nom du Médecin. Clé MD5 avec sel `MEDWIN_SEC_2026`. Format : `XXXX-XXXX-XXXX-XXXX`.
   - **MailPocket Pro** : Nom, Prénom, N° d'Ordre, Gouvernorat/Ville. Clé cryptographique format : `MED-ORDRE-NOMPRENOM-LIEU-SIGNATURE`.
   - **ComptaPocket SMS** : Nom du Bureau Comptable / Expert. Clé MD5 avec sel `COMPTA_SEC_2026`. Format : `XXXX-XXXX-XXXX-XXXX`.
   - **DocPocket Pro (Universel)** : Nom du Médecin. Clé Base64 sécurisée format : `DOCPRO-[Base64]-2026`.
   - **FinPocket** : Nom du Praticien / Cabinet, N° Ordre / Matricule, Postes (1, 3, 5), Durée. Clé format : `FIN-XXXX-XXXX-XXXX-XXXX`.
   - **GlycoPocket** : Nom du Médecin / Diabétologue, N° Ordre, Spécialité, Durée. Clé format : `GLYCO-XXXX-XXXX-XXXX-XXXX`.

3. **🔥 Synchronisation Firebase Realtime Database :**
   - Synchronisation bidirectionnelle directe avec Firebase (`/docpocket_licenses_registry`).
   - Sauvegarde automatique en direct dès la délivrance d'une nouvelle licence.
   - Fonctionne également en mode **100% hors-ligne (Stockage Local)** si aucune base distante n'est configurée.

4. **📋 Registre & Historique Global :**
   - Suivi centralisé de toutes les licences générées, toutes applications confondues.
   - Filtre instantané par application et barre de recherche multicritère.
   - Modification de statut en 1 clic (*Actif*, *Révoqué*).
   - Export en **CSV** (compatible Excel) et **Backup JSON**.
   - Restauration de base à partir d'un fichier JSON.

5. **💬 Outils de Partage Rapide :**
   - **Copier la clé** dans le presse-papiers avec feedback visuel immédiat.
   - **Partager via WhatsApp** avec un message pré-rédigé personnalisé contenant les instructions d'activation.
   - **Envoyer par Email** prêt à l'envoi vers le praticien.

6. **⚡ Support PWA & Fonctionnement 100% Hors-Ligne :**
   - Manifeste complet (`manifest.json`) permettant l'installation sur bureau (Chrome, Edge) et mobile (Android, iOS).
   - Service Worker (`sw.js`) pour la mise en cache intégrale des fichiers sans nécessiter de connexion internet.
   - Cryptographie autonome embarquée (MD5 et SHA-256 purs) sans dépendance CDN externe.

---

## 💻 Démarrage & Utilisation

### Option 1 : Ouvrir directement dans le navigateur
Double-cliquez simplement sur le fichier `index.html` pour ouvrir la console dans votre navigateur habituel.

### Option 2 : Lancer un serveur local (Recommandé pour tester le Service Worker PWA)
Dans un terminal PowerShell ou Invite de commandes situé dans ce dossier :
```powershell
npx serve -l 8080 .
# ou via Python :
python -m http.server 8080
```
Puis accédez à `http://localhost:8080` dans Google Chrome ou Microsoft Edge, et cliquez sur l'icône **"Installer l'application"** dans la barre d'adresse pour l'installer en tant qu'application autonome sur votre bureau.

---

## 📁 Structure des Fichiers

- `index.html` : Interface complète, styles CSS glassmorphism, formulaires, registre unifié et logique cryptographique.
- `manifest.json` : Configuration PWA (icônes, nom, couleurs du thème).
- `sw.js` : Service Worker pour le cache hors-ligne.
- `icon-192.png` & `icon-512.png` : Icônes haute définition de l'application.
- `logo.png` : Logo officiel pour l'écran de verrouillage.
