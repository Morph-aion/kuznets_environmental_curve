# 🌍 Projet : Courbe de Kuznets Environnementale (EKC) & Croissance

Ce dépôt contient l'ensemble du travail collaboratif pour notre rapport académique, visant à tester empiriquement l'hypothèse de la Courbe de Kuznets Environnementale (relation entre croissance économique et dégradation environnementale).

---

## 🏁 Démarrage Rapide

**1. Installation**
```bash
pip install -r requirements.txt
quarto install tinytex  # Nécessaire pour le PDF
```

**2. Génération du Rapport**
Ce projet utilise des **profils Quarto**. Ne lancez pas `quarto render` seul.

*   **🇫🇷 Version Française :**
    ```bash
    quarto render --profile fr --to pdf
    ```
    📂 Résultat : `output/fr/_book/`

*   **🇺🇸 Version Anglaise :**
    ```bash
    quarto render --profile en --to pdf
    ```
    📂 Résultat : `output/en/_book/`

---

## 🤝 Notre philosophie de travail

> **Rigueur économétrique et clarté interprétative.**

Nous partageons :
- Une **structure commune** pour faciliter la fusion des parties (Introduction, Revue de litt, Modélisation, Résultats).
- Des **outils statistiques robustes** pour valider nos hypothèses (Tests de racine unitaire, cointégration, etc.).
- Une **cohérence des données** : on s'assure que tout le monde utilise les mêmes unités (ex: $CO_2$ en tonnes métriques par habitant).
- Une **bienveillance mutuelle** : la modélisation est itérative, on discute des choix de spécification (linéaire, quadratique ou cubique).

---

## 🗂️ Structure du Projet — En 30 secondes

```
ekc_analysis_project/
├── data/                 # Données (WDI, OCDE, etc.) → raw / processed
├── notebooks/            # Laboratoire d'économétrie (un dossier par étape)
├── content/              # Rapport final (.qmd) - Rédaction académique
├── assets/               # Graphiques exportés, schémas, biblio (.bib)
├── models/               # Résultats des régressions sauvegardés (ex: tables pickle/latex)
├── documentation/        # Papiers de recherche de référence, définitions des variables
├── project-management/   # Timeline et répartition des tâches
└── output/_book/         # Le rapport PDF final compilé
```

→ **Pourquoi cette structure ?**
Parce qu’elle sépare clairement :
- La **préparation des données** (gestion des valeurs manquantes, logarithmes),
- L’**estimation** (notebooks de tests économétriques),
- La **rédaction** (interprétation économique dans le dossier content).

---

## 🚀 Workflow Recommandé

1. **Expérimentez dans les notebooks** → Testez les modèles (OLS, Effets Fixes, GMM).
2. **Sauvegardez vos artefacts** :
   - Données nettoyées (avec log et carrés calculés) → `data/03_processed/`
   - Tableaux de régression (format LaTeX) → `assets/tables/`
   - Graphiques de la courbe en U → `assets/images/`
3. **Intégrez dans le `.qmd`** :
   - Importez les tableaux et graphiques.
   - Commentez les signes des coefficients ($\beta_1 > 0$, $\beta_2 < 0$ ?).
4. **Compilez avec Quarto** → Pour vérifier la mise en page des équations mathématiques.

---

## ⚙️ Outils Stratégiques — Pour une économétrie robuste

### ► Statsmodels & Linearmodels : Notre "boîte à outils"
- Emplacement : `notebooks/04-estimation-modeles/`
- Objectif : Estimer les équations (Panel FE/RE, Séries temporelles).
- **Point clé** : Ne pas se contenter du $R^2$. Vérifier la significativité des coefficients des termes au carré (`ln(PIB/hab)^2`) et au cube.

### ► Tests de Diagnostic : Notre "contrôle qualité"
- Emplacement : `notebooks/05-tests-diagnostics/`
- Objectif : Valider que nos résultats ne sont pas "fallacieux" (Spurious regression).
- **À vérifier** :
    - Hétéroscédasticité (Breusch-Pagan).
    - Autocorrélation des résidus.
    - Stationnarité (Tests de Racine Unitaire : ADF, IPS, Levin-Lin-Chu).
    - Cointégration (si les séries sont non-stationnaires).

---

## 🤝 Comment bien collaborer ?

- **Notation mathématique unifiée** : On utilise tous `\ln(\ce{CO2}/\text{hab})` et non `log(CO2)` dans le texte.
- **Justifiez les choix** : Pourquoi avoir choisi ce pays ? Pourquoi cette période ? (Notez-le dans le notebook).
- **Données manquantes** : On se met d'accord sur la méthode d'imputation ou d'exclusion *avant* de lancer les régressions.
- **Reproductibilité** : Si vous filtrez des données (ex: suppression des outliers), le code doit être explicite.

---

## 📅 Timeline & Coordination

Les fichiers dans `project-management/` permettent de suivre qui rédige la revue de littérature et qui gère la partie empirique.

> 👉 **Prochaine étape** : Valider la liste des pays et la période temporelle pour la base de données finale.

---

## ❓ Besoin d’aide ?
Si vous bloquez sur une erreur LaTeX ou un test de Hausman qui échoue, envoyez un message.
On est là pour comprendre les dynamiques économiques — ensemble.

Bonne analyse à tous ! 📉📈
