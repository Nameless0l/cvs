# CV & Lettre de Motivation Generator (IA + LaTeX)

Système de génération automatique de **CV** et **Lettres de Motivation** en LaTeX, piloté par IA (GitHub Copilot / Claude). Chaque candidature est ciblée selon l'offre d'emploi : l'IA sélectionne les expériences pertinentes, adapte le ton, les couleurs et les compétences mises en avant.

## Principe

Tu fournis une offre d'emploi (texte, lien, ou description). L'IA génère un `.tex` prêt à compiler avec :

- Les 3-4 expériences les plus pertinentes pour le poste
- Une accroche ciblée avec le nom de l'entreprise
- Les compétences techniques regroupées par catégorie
- Les couleurs adaptées à l'entreprise cible
- Un format 1 page (CV) ou lettre classique (LM)

## Structure du projet

```
cvs/
├── .github/
│   ├── copilot-instructions.md   # Instructions IA (source de vérité)
│   └── agents/
│       └── agents_cv_ia.agent.md # Agent spécialisé VS Code
├── .claude/
│   └── settings.local.json      # Config Claude Code (compilation LaTeX)
├── CLAUDE.md                     # Instructions pour Claude Code
├── cv_actuel.tex                 # Template CV de base
├── resume.cls                    # Classe LaTeX alternative (style US)
├── Makefile                      # Nettoyage fichiers auxiliaires
├── examples/                    # Exemples de candidatures générées
├── cv_loic_*_<poste>_<entreprise>.tex   # CVs générés
└── lm_loic_*_<poste>_<entreprise>.tex   # Lettres de motivation générées
```

## Comment adapter ce projet pour toi

### 1. Fork et clone le repo

```bash
git clone https://github.com/<ton-username>/cvs.git
cd cvs
```

### 2. Remplace les informations personnelles

Dans `.github/copilot-instructions.md` (et `CLAUDE.md` si tu utilises Claude Code), remplace la section **0.1 INFORMATIONS PERSONNELLES** :

```latex
\newcommand{\MonNom}{Ton Nom Complet}
\newcommand{\MonEmail}{ton.email@exemple.fr}
\newcommand{\MonTelephone}{(+33) X XX XX XX XX}
\newcommand{\MonAdresse}{Ta Ville, France}
\newcommand{\MonLinkedin}{https://www.linkedin.com/in/ton-profil/}
\newcommand{\MonGithub}{https://github.com/ton-username}
\newcommand{\MonPortfolio}{https://ton-site.com}
```

Mets aussi à jour les disponibilités (stage, alternance, dates).

### 3. Remplace la base de données d'expériences

C'est la partie la plus importante. Dans la **section 3** du fichier d'instructions, remplace toutes les expériences par les tiennes. Pour chaque expérience, renseigne :

```markdown
- **Titre du poste @ Entreprise** | _Dates_ | _Lieu_
  - _Domaine:_ Secteur d'activité
  - _Tech:_ Technologies utilisées
  - _Réalisations:_ Ce que tu as fait (Action -> Résultat concret)
```

Sois exhaustif : l'IA sélectionnera intelligemment les plus pertinentes selon chaque offre.

### 4. Adapte le tableau de mapping

La **section 4** contient un tableau qui guide l'IA dans la sélection des expériences selon le type d'offre. Adapte-le à ton profil :

```markdown
| Type d'offre       | Expériences à prioriser          | Compétences clés        |
| ------------------- | -------------------------------- | ----------------------- |
| **Full Stack / Web** | Ton projet 1, Ton projet 2       | React, Node.js, Docker  |
| **IA / ML**          | Ton stage ML, Ton projet IA      | PyTorch, Python, NLP    |
```

### 5. Ajoute les couleurs de tes entreprises cibles

```latex
% Google    : {RGB}{66, 133, 244}
% Amazon    : {RGB}{255, 153, 0}
% Meta      : {RGB}{24, 119, 242}
% Default   : {RGB}{35, 55, 123}
```

### 6. (Optionnel) Ajoute tes leçons apprises

La **section 8** contient un retour d'expérience sur les candidatures rejetées. C'est un mécanisme d'amélioration continue : après chaque rejet, note ce qui n'a pas fonctionné pour que l'IA ne refasse pas les mêmes erreurs.

## Utilisation

### Avec GitHub Copilot (VS Code)

1. Ouvre le projet dans VS Code avec l'extension GitHub Copilot
2. Utilise l'agent `@agents_cv_ia` dans le chat ou demande directement :

```
Génère un CV et une LM pour cette offre :
[coller l'offre d'emploi ici]
```

3. L'IA génère les fichiers `.tex` ciblés
4. Compile avec `pdflatex` ou ton éditeur LaTeX

### Avec Claude Code

```bash
claude "Génère un CV pour cette offre : [description de l'offre]"
```

### Compilation LaTeX

```bash
# Compiler un CV
pdflatex cv_nom_poste_entreprise.tex

# Nettoyer les fichiers auxiliaires
make clean        # CMD
make clean-ps     # PowerShell
```

### Convention de nommage

- CV : `cv_prenom_nom_<poste>_<entreprise>.tex`
- LM : `lm_prenom_nom_<poste>_<entreprise>.tex`

## Prérequis

- **LaTeX** : TeX Live, MiKTeX ou MacTeX
- **Packages LaTeX** : `fontawesome5`, `hyperref`, `xcolor`, `titlesec`, `enumitem`, `lmodern`, `ulem`
- **VS Code** + GitHub Copilot (recommandé) ou Claude Code

## Règles de rédaction intégrées

L'IA suit des règles strictes pour produire des candidatures de qualité :

- Ton ingénieur, orienté résultats (Action -> Résultat)
- Pas d'adjectifs vides ("passionné", "motivé", "dynamique")
- Sélection ciblée : 3-4 expériences pertinentes, pas un catalogue
- Chaque bullet point répond à un mot-clé de l'offre
- CV = 1 page max

## Licence

Usage personnel. Adaptez librement pour vos propres candidatures.
