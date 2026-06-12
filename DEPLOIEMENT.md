# Guide de déploiement — GitHub Pages

Mise en ligne du site **Palette pour Marie-Madeleine Martinet**  
Environnement : **Windows 10 · VS Code · GitHub** (débutant)

---

## Prérequis

- [ ] Compte GitHub — [github.com](https://github.com) (gratuit)
- [ ] Git pour Windows — [git-scm.com/download/win](https://git-scm.com/download/win)  
      *(VS Code détecte Git automatiquement après l'installation)*
- [ ] VS Code ouvert sur le dossier du site

---

## Étape 1 — Créer le dépôt sur GitHub

1. Connectez-vous à [github.com](https://github.com)
2. Cliquez **+** (en haut à droite) → **New repository**
3. Remplissez :
   - **Repository name** : `palette-mmm` *(ou le nom de votre choix)*
   - **Visibility** : ✅ **Public** *(obligatoire pour GitHub Pages gratuit)*
   - **Initialize** : laissez **décoché** *(on pousse les fichiers depuis votre PC)*
4. Cliquez **Create repository**
5. GitHub affiche votre URL : `https://github.com/VOTRE-USERNAME/palette-mmm`  
   → **Copiez-la**, vous en aurez besoin à l'étape 3.

---

## Étape 2 — Préparer le dossier local

1. Décompressez l'archive `mmm_rct-suite1-leonardo.zip` dans un dossier dédié,  
   par exemple : `C:\Projets\palette-mmm\`
2. Vérifiez que `index.html` est bien à la **racine** de ce dossier  
   *(pas dans un sous-dossier)*
3. Vérifiez que `.nojekyll` est aussi présent à la racine

---

## Étape 3 — Initialiser Git et pousser vers GitHub

### Option A — Via VS Code *(recommandé pour débuter)*

1. **Fichier → Ouvrir le dossier** → `C:\Projets\palette-mmm\`
2. Cliquez l'icône **Contrôle de code source** dans la barre latérale gauche  
   *(icône en forme de branchement, 3ᵉ en partant du haut)*
3. Cliquez **Initialiser le dépôt**
4. Tous les fichiers apparaissent dans la liste des modifications
5. Entrez le message : `Premier commit — site Palette MMM`  
   puis cliquez **✓ Valider** *(ou Ctrl+Entrée)*
6. Cliquez **Publier la branche** *(bouton bleu, barre de statut en bas)*
7. Si demandé, connectez-vous à GitHub dans le navigateur
8. Choisissez **Publier sur GitHub Public** → nom : `palette-mmm`
9. VS Code pousse les fichiers ✓

### Option B — Via PowerShell *(ligne de commande)*

```powershell
cd C:\Projets\palette-mmm
git init
git add .
git commit -m "Premier commit — site Palette MMM"
git branch -M main
git remote add origin https://github.com/VOTRE-USERNAME/palette-mmm.git
git push -u origin main
```

---

## Étape 4 — Activer GitHub Pages

1. Sur GitHub, ouvrez votre dépôt `palette-mmm`
2. Cliquez l'onglet **Settings** (roue dentée, à droite)
3. Dans le menu gauche, cliquez **Pages**
4. Sous **Build and deployment → Source** : sélectionnez **Deploy from a branch**
5. Sous **Branch** : choisissez `main` et le dossier `/ (root)`
6. Cliquez **Save**
7. Attendez **1 à 2 minutes** — un bandeau vert s'affiche avec l'URL du site :

```
https://VOTRE-USERNAME.github.io/palette-mmm/
```

---

## Étape 5 — Vérifier le rendu en ligne

- [ ] La page d'accueil (`index.html`) s'affiche
- [ ] La navigation par zones fonctionne (clic sur les couleurs)
- [ ] Le lien vers le PDF Léonard de Vinci s'ouvre
- [ ] Testez une URL inexistante → la page **404 personnalisée** doit apparaître
- [ ] Testez sur mobile/tablette (versions `_s` et `_t`)

---

## Étape 6 — Mettre à jour le site (modifications futures)

1. Modifiez les fichiers dans `C:\Projets\palette-mmm\`
2. Dans VS Code → Contrôle de code source → message de commit → **Valider**
3. Cliquez **Synchroniser les modifications** (↑↓ dans la barre de statut)
4. GitHub Pages redéploie automatiquement *(délai : 1-2 min)*

Vous pouvez suivre le déploiement dans l'onglet **Actions** de votre dépôt.

---

## Résolution des problèmes fréquents

| Symptôme | Cause | Solution |
|---|---|---|
| Page 404 sur l'accueil | `index.html` absent de la racine | Vérifier l'emplacement du fichier |
| Images manquantes | Casse de nom de fichier | GitHub Pages est sensible à la casse — vérifier majuscules/minuscules |
| Site non mis à jour | Cache navigateur | `Ctrl + Maj + R` pour forcer le rechargement |
| Mise en page dégradée | Jekyll actif | Vérifier que `.nojekyll` est bien dans le dépôt (fichier visible dans VS Code) |
| Délai d'affichage | Build en cours | Attendre 2-5 min · consulter l'onglet **Actions** |

---

> 💡 **Pour un domaine personnalisé** (ex. `mmm.sorbonne.fr`) : ajoutez un fichier `CNAME`
> à la racine avec l'URL cible, et configurez votre DNS. Ce n'est pas obligatoire pour démarrer.
