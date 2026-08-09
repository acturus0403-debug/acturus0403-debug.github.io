# Vint'Hess

Petite marketplace communautaire fictive avec React + Vite + Tailwind + Supabase.

Important:
- Pas de paiement.
- Pas d'achat sur le site.
- Les utilisateurs publient et gerent uniquement leurs annonces.

## 1. Creer un projet Supabase gratuit
1. Va sur https://supabase.com et cree un compte.
2. Clique sur **New project**.
3. Choisis un nom de projet, un mot de passe de base de donnees, et une region.
4. Attends que le projet soit pret.

## 2. Copier le SQL dans Supabase
1. Ouvre ton projet Supabase.
2. Va dans **SQL Editor**.
3. Ouvre le fichier `supabase/schema.sql` de ce projet.
4. Copie tout le contenu.
5. Colle dans SQL Editor puis clique sur **Run**.

## 3. Creer/configurer le bucket photos
Si tu as execute `schema.sql`, le bucket est deja cree automatiquement.

Si besoin manuel:
1. Va dans **Storage**.
2. Cree un bucket nomme `listing-images`.
3. Mets-le en **Public**.
4. Les policies Storage sont deja dans `schema.sql`.

## 4. Recuperer SUPABASE_URL et la cle publique anon
1. Va dans **Project Settings** > **API**.
2. Copie:
- **Project URL**
- **anon public key**

Ne jamais utiliser de `service_role` dans le frontend.

## 5. Renseigner les variables d'environnement
1. A la racine du projet, copie `.env.example` en `.env.local`.
2. Remplace les valeurs:
- `VITE_SUPABASE_URL`
- `VITE_SUPABASE_ANON_KEY`
- `VITE_SUPABASE_LISTING_BUCKET` (garde `listing-images`)

## 6. Tester le site en local
1. Installe les dependances:
`npm install`
2. Lance le projet:
`npm run dev`
3. Ouvre l'URL locale affichee dans le terminal.

## 7. Pousser les fichiers sur GitHub
1. Cree un repo GitHub.
2. Dans ton terminal:
`git init`
`git add .`
`git commit -m "Vint'Hess initial"`
`git branch -M main`
`git remote add origin TON_URL_DU_REPO`
`git push -u origin main`

## 8. Activer GitHub Pages
Option simple (sans action automatique):
1. Lance `npm run build`.
2. Cree un dossier `docs` a la racine.
3. Copie le contenu de `dist` dans `docs`.
4. Commit + push.
5. Sur GitHub: **Settings** > **Pages**.
6. Dans **Source**, choisis **Deploy from a branch**.
7. Selectionne branche `main` et dossier `/docs`.
8. Sauvegarde et attends le lien public.

Le projet utilise `HashRouter`, donc les routes fonctionnent sur GitHub Pages meme en sous-chemin.

## 9. Mettre le site a jour plus tard
1. Modifie ton code.
2. Teste avec `npm run dev`.
3. Build avec `npm run build`.
4. Recopie `dist` vers `docs`.
5. `git add .`
6. `git commit -m "Mise a jour"`
7. `git push`

## Notes utiles
- Les images sont stockees dans Supabase Storage.
- Les droits de lecture/ecriture sont proteges avec RLS.
- Les favoris sont prives par utilisateur.