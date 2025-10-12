<!--
CO_OP_TRANSLATOR_METADATA:
{
  "original_hash": "913da05fee7fb78699c0447cf6d8aa10",
  "translation_date": "2025-10-12T09:23:25+00:00",
  "source_file": "AGENTS.md",
  "language_code": "fr"
}
-->
# AGENTS.md

## Aperçu du projet

**Security-101** est un programme d'apprentissage en cybersécurité destiné aux débutants, créé par Microsoft. Ce projet est une ressource pédagogique basée sur la documentation qui enseigne les concepts fondamentaux de la cybersécurité à travers des modules structurés. Il est indépendant des fournisseurs et conçu pour être complété en petites leçons (30 à 60 minutes chacune).

**Technologies clés :**
- Markdown pour le contenu
- Docsify pour la génération de sites statiques
- GitHub Pages pour l'hébergement
- Co-op Translator pour le support multilingue (50+ langues)
- GitHub Actions pour CI/CD

**Architecture :**
- Contenu éducatif organisé en 8 modules principaux, chacun avec des sous-leçons
- Site HTML statique avec Docsify pour le rendu du contenu Markdown
- Flux de traduction automatisé utilisant les services Azure AI
- Aucun outil de construction ou gestionnaire de paquets requis pour le contenu principal

## Structure du dépôt

```
/
├── README.md                    # Main entry point with curriculum overview
├── index.html                   # Docsify site entry point
├── [1-8].[1-4] *.md            # Curriculum modules and lessons
├── CODE_OF_CONDUCT.md          # Community guidelines
├── SECURITY.md                 # Security policy
├── SUPPORT.md                  # Support information
├── LICENSE                     # MIT License
├── images/                     # Image assets for lessons
├── translated_images/          # Translated image assets
├── translations/               # Translated versions (50+ languages)
└── .github/
    ├── workflows/
    │   ├── co-op-translator.yml    # Automated translation workflow
    │   ├── deploy.yaml             # GitHub Pages deployment
    │   └── jekyll-gh-pages.yml     # Jekyll site generation
    └── ISSUE_TEMPLATE/             # Issue templates
```

## Commandes d'installation

Il s'agit d'un projet de documentation sans dépendances à installer. Pour travailler avec le contenu :

```bash
# Clone the repository
git clone https://github.com/microsoft/Security-101.git
cd Security-101

# View content locally - any Markdown viewer works
# OR serve with a simple HTTP server to use Docsify rendering
python -m http.server 8000
# Then visit http://localhost:8000 in your browser
```

## Flux de développement

### Visualisation du contenu en local

Le projet utilise Docsify pour le rendu. Pour prévisualiser les modifications :

```bash
# Option 1: Use Python's built-in HTTP server
python -m http.server 8000

# Option 2: Use Node.js http-server (if available)
npx http-server -p 8000

# Option 3: View Markdown files directly in any Markdown editor
```

### Structure du contenu

Les modules sont numérotés séquentiellement :
- **Module 1 :** Concepts de base en sécurité (1.1-1.7)
- **Module 2 :** Gestion des identités et des accès (2.1-2.4)
- **Module 3 :** Sécurité réseau (3.1-3.4)
- **Module 4 :** Opérations de sécurité (4.1-4.4)
- **Module 5 :** Sécurité des applications (5.1-5.3)
- **Module 6 :** Sécurité des infrastructures (6.1-6.3)
- **Module 7 :** Sécurité des données (7.1-7.3)
- **Module 8 :** Sécurité de l'IA (8.1-8.4)

Chaque module se termine par un fichier de quiz (par exemple, "1.7 Quiz de fin de module.md").

### Modification du contenu

1. Modifier directement les fichiers Markdown dans le répertoire racine
2. Suivre la convention de nommage existante : `[module].[lesson] [Titre].md`
3. Mettre à jour le tableau dans README.md si des modules sont ajoutés ou supprimés
4. Ajouter des images dans le répertoire `/images/`
5. Référencer les images en utilisant des chemins relatifs : `![Description](../../translated_images/nom_du_fichier.dc67434800a09b2caf541474e8f05a389a1a7871be12415ed2192c56d0f2acd2.fr.png)`

## Flux de traduction

**Traduction automatisée :**
- Les traductions sont gérées automatiquement par l'action GitHub Co-op Translator
- Lorsque vous poussez des modifications sur la branche `main`, le flux traduit le contenu en plus de 50 langues
- Les fichiers traduits sont stockés dans `/translations/[language_code]/`
- Les métadonnées de traduction sont conservées dans le frontmatter YAML

**Langues prises en charge :** Arabe, Bengali, Bulgare, Birman, Chinois (simplifié, traditionnel), Croate, Tchèque, Danois, Néerlandais, Estonien, Finnois, Français, Allemand, Grec, Hébreu, Hindi, Hongrois, Indonésien, Italien, Japonais, Coréen, Lituanien, Malais, Marathi, Népalais, Norvégien, Persan, Polonais, Portugais, Punjabi, Roumain, Russe, Serbe, Slovaque, Slovène, Espagnol, Swahili, Suédois, Tagalog, Tamoul, Thaï, Turc, Ukrainien, Ourdou, Vietnamien, et plus encore.

**Ne modifiez PAS manuellement les fichiers de traduction** - ils seront écrasés par le flux automatisé.

## Directives de style de code

### Conventions Markdown

- Utiliser la syntaxe standard Markdown
- Titres : Utiliser `#` pour le titre principal, `##` pour les sections, `###` pour les sous-sections
- Listes : Utiliser `-` ou `*` pour les listes non ordonnées, `1.` pour les listes ordonnées
- Liens : Utiliser un texte descriptif avec des URL GitHub complètes pour les références croisées
- Images : Stocker dans le répertoire `/images/`, utiliser un texte alternatif descriptif
- Blocs de code : Utiliser des triples backticks avec un identifiant de langage lorsque c'est applicable

### Directives de contenu

- Garder les leçons concises et ciblées (30 à 60 minutes de lecture)
- Utiliser un langage clair et adapté aux débutants
- Éviter les instructions spécifiques aux outils des fournisseurs (le programme est indépendant des fournisseurs)
- Inclure des objectifs d'apprentissage au début de chaque module
- Lier des ressources externes Microsoft Learn lorsque c'est approprié
- S'assurer que le contenu est éducatif, non promotionnel

### Nommage des fichiers

- Utiliser le format : `[Module].[Lesson] [Titre].md`
- Exemple : `1.1 La triade CIA et autres concepts clés.md`
- Fichiers de quiz : `[Module].[Last] Quiz de fin de module.md`
- Utiliser des espaces dans les noms de fichiers (convention existante)

## Flux GitHub

### Co-op Translator (co-op-translator.yml)

**Déclencheur :** Push sur la branche `main`  
**Objectif :** Traduire automatiquement les fichiers Markdown nouveaux/modifiés en plus de 50 langues

**Variables d'environnement requises :**
- Identifiants du service Azure AI (AZURE_AI_SERVICE_API_KEY, AZURE_AI_SERVICE_ENDPOINT)
- Identifiants Azure OpenAI (alternative optionnelle)
- Identifiants OpenAI (alternative optionnelle)

### Déploiement (deploy.yaml)

**Déclencheur :** Push sur la branche `main` lorsque README.md est modifié  
**Objectif :** Déploie le site statique sur GitHub Pages  
**Résultat :** Met à jour le site GitHub Pages

### Jekyll GitHub Pages (jekyll-gh-pages.yml)

**Déclencheur :** Push sur la branche configurée  
**Objectif :** Construit et déploie le site en utilisant Jekyll

## Directives pour les pull requests

### Avant de soumettre

1. **Revue du contenu :** Vérifier l'exactitude et la clarté des concepts de cybersécurité
2. **Formatage :** Vérifier que le formatage Markdown s'affiche correctement
3. **Liens :** Tester tous les liens internes et externes
4. **Images :** S'assurer que toutes les images se chargent et ont un texte alternatif descriptif
5. **Cohérence :** Suivre la structure et le style de contenu existants

### Format des titres de PR

Utiliser des titres descriptifs :
- `Ajout : [Description du nouveau contenu]`
- `Mise à jour : [Module/Leçon] - [Brève description]`
- `Correction : [Description du problème]`
- `Docs : [Modifications de la documentation]`

### Vérifications requises

- Exactitude du contenu (revue manuelle)
- Validation du formatage Markdown
- Vérification des liens
- Achèvement du flux de traduction (pour les fusions dans la branche `main`)

### Processus de revue

1. Au moins une revue par un mainteneur est requise
2. Se concentrer sur l'exactitude technique des concepts de sécurité
3. Vérifier l'accessibilité et l'adaptation aux débutants
4. S'assurer que la neutralité vis-à-vis des fournisseurs est maintenue

## Tâches courantes

### Ajouter une nouvelle leçon

```bash
# 1. Create new Markdown file with proper naming
touch "[Module].[Lesson] [Title].md"

# 2. Add content following template structure
# 3. Update README.md module table with new entry
# 4. Add entry to module overview table
# 5. Ensure quiz file numbering is correct

# 6. Commit changes
git add "[Module].[Lesson] [Title].md" README.md
git commit -m "Add: [Module].[Lesson] - [Title]"
git push
```

### Mettre à jour le contenu existant

```bash
# 1. Edit the relevant Markdown file
# 2. Verify formatting and links
# 3. Commit with descriptive message
git add "[Module].[Lesson] [Title].md"
git commit -m "Update: [Module].[Lesson] - [Brief description of changes]"
git push
```

### Ajouter des images

```bash
# 1. Add image to /images/ directory
cp new-image.png images/

# 2. Reference in Markdown
# ![Descriptive alt text](../../translated_images/new-image.ade387a7c819665dda19f7585b9b1cc82817a21d283e286f39c2891d201fcdab.fr.png)

# 3. Commit both content and image
git add "images/new-image.png" "[Module].[Lesson] [Title].md"
git commit -m "Add: Image for [description]"
git push
```

## Tests et validation

### Validation du contenu

Étant donné qu'il s'agit d'un projet de documentation, les tests se concentrent sur :

1. **Rendu Markdown :** Visualiser les modifications en local avec Docsify
2. **Validation des liens :** Cliquer manuellement sur tous les liens
3. **Chargement des images :** Vérifier que toutes les images s'affichent correctement
4. **Traduction :** Vérifier que les fichiers sont pris en charge par le flux de traduction (automatisé)
5. **Accessibilité :** S'assurer de la hiérarchie correcte des titres et du texte alternatif

### Prévisualisation locale

```bash
# Serve locally to test Docsify rendering
python -m http.server 8000

# Visit http://localhost:8000
# Click through navigation to verify all links work
# Check that images load properly
# Verify Markdown formatting renders correctly
```

### Liste de vérification avant commit

- [ ] Les fichiers Markdown utilisent la syntaxe correcte
- [ ] Tous les liens sont valides et utilisent HTTPS lorsque c'est possible
- [ ] Les images ont un texte alternatif descriptif
- [ ] Le contenu est adapté aux débutants et exact
- [ ] Le langage neutre vis-à-vis des fournisseurs est maintenu
- [ ] README.md mis à jour si des modules sont ajoutés ou supprimés
- [ ] Le nom des fichiers suit les conventions

## Considérations de sécurité

- **Pas de secrets dans le contenu :** Ne jamais commettre de clés API, mots de passe ou données sensibles
- **Validation des liens :** S'assurer que tous les liens externes pointent vers des sources fiables
- **Contenu des images :** Vérifier que les images ne contiennent pas d'informations sensibles
- **Flux de traduction :** Utilise les services Azure AI avec une authentification appropriée
- **SECURITY.md :** Suivre le processus de signalement des vulnérabilités dans SECURITY.md

## Ressources supplémentaires

### Cours Microsoft associés

Ce programme fait partie d'une collection plus large de ressources éducatives Microsoft :
- IA générative pour les débutants
- IA pour les débutants
- Science des données pour les débutants
- Apprentissage automatique pour les débutants
- Développement web pour les débutants
- IoT pour les débutants

### Parcours d'apprentissage externes

Après avoir terminé Security-101 :
- [Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/training/paths/describe-concepts-of-security-compliance-identity/)
- [Examen SC-900 : Microsoft Security, Compliance, and Identity Fundamentals](https://learn.microsoft.com/credentials/certifications/exams/sc-900/)

## Contribution

1. **Forker le dépôt** sur GitHub
2. **Créer une branche de fonctionnalité** pour vos modifications
3. **Apporter vos modifications** en suivant les directives ci-dessus
4. **Tester en local** pour s'assurer que tout s'affiche correctement
5. **Soumettre une pull request** avec une description claire des modifications
6. **Répondre aux commentaires** des mainteneurs

## Problèmes courants et dépannage

### Traductions ne fonctionnent pas

- S'assurer que les modifications sont poussées sur la branche `main`
- Vérifier l'onglet GitHub Actions pour le statut du flux
- Vérifier que les secrets du flux de traduction sont configurés
- La traduction est automatique ; ne modifiez pas manuellement les fichiers de traduction

### Images ne se chargent pas

- Vérifier que le chemin de l'image utilise des barres obliques : `images/nom_du_fichier.png`
- Vérifier que le fichier image est commis dans le dépôt
- S'assurer que le nom du fichier image correspond exactement (sensible à la casse)
- Utiliser des chemins relatifs, pas des URL absolues

### Docsify ne rend pas

- Vérifier que `index.html` est présent dans le répertoire racine
- Vérifier que les liens CDN de Docsify sont accessibles
- S'assurer que les fichiers Markdown utilisent une syntaxe standard
- Vérifier la console du navigateur pour les erreurs JavaScript

### Liens ne fonctionnent pas

- Utiliser des URL GitHub complètes pour les références croisées entre les leçons
- Format : `https://github.com/microsoft/Security-101/blob/main/[file].md`
- Tester les liens dans la vue rendue, pas seulement dans le Markdown brut

## Maintenance du projet

### Tâches régulières

- Revoir et fusionner les contributions de la communauté
- Mettre à jour le contenu pour garantir son exactitude à mesure que le paysage de la sécurité évolue
- Surveiller les erreurs dans le flux de traduction
- Répondre aux problèmes et discussions
- Maintenir les liens externes à jour

### Contrôle de version

- La branche `main` est protégée et nécessite des revues de PR
- Toutes les modifications passent par le processus de pull request
- Les fichiers de traduction sont générés automatiquement, ne pas les modifier manuellement
- Utiliser des messages de commit significatifs

## Notes pour les agents IA de codage

- **Il s'agit d'un projet de documentation** - se concentrer sur la qualité du contenu, pas sur le code
- **Ne pas modifier les fichiers de traduction** - ils sont générés automatiquement
- **Respecter les conventions de nommage des fichiers** - utiliser des espaces dans les noms de fichiers selon le modèle existant
- **Mettre à jour README.md** lors de l'ajout ou de la suppression de modules pour garder le tableau synchronisé
- **Tester en local** avant de soumettre des PR pour s'assurer que le Markdown s'affiche correctement
- **Suivre le style de contenu existant** - maintenir un ton adapté aux débutants et neutre vis-à-vis des fournisseurs
- **Aucun processus de construction requis** - un simple serveur HTTP suffit pour le développement local
- **Respecter la structure des modules** - chaque module a une numérotation et une organisation cohérentes

---

**Avertissement** :  
Ce document a été traduit à l'aide du service de traduction automatique [Co-op Translator](https://github.com/Azure/co-op-translator). Bien que nous nous efforcions d'assurer l'exactitude, veuillez noter que les traductions automatisées peuvent contenir des erreurs ou des inexactitudes. Le document original dans sa langue d'origine doit être considéré comme la source faisant autorité. Pour des informations critiques, il est recommandé de recourir à une traduction humaine professionnelle. Nous déclinons toute responsabilité en cas de malentendus ou d'interprétations erronées résultant de l'utilisation de cette traduction.