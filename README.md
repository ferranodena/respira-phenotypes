# Respira Hackathon: Beyond the Infection, a Smart Map to Understand Sequelae

🏆 **First prize winner** of the challenge *"Más allá de la infección: un mapa inteligente para comprender las secuelas"*.

Developed during the Respira Hackathon, organised by the Centro de Investigación Biomédica en Red (CIBER) and AstraZeneca, with a focus on the respiratory research area CIBERES.

## The challenge

Recovery after a severe respiratory infection varies a lot between patients. Some return to their previous health. Others live for months or years with dyspnoea, fatigue, memory or concentration problems, sleep disturbances or muscle weakness. Current classifications usually focus on isolated symptoms or abnormalities. They can group patients with very different recovery needs under one diagnosis.

The challenge was to build an AI and data-analysis prototype that turns clinical, functional, radiological and follow-up data into a **map of patient profiles (phenotypes)**. The tool had to:

- identify groups of patients with similar characteristics and recovery trajectories;
- describe in plain language what defines each group;
- show the results clearly and visually to clinicians and researchers.

## Our approach

We worked with anonymised multimodal data from several cohorts:

- **CIBERES**: ICU patients from the first COVID-19 waves, followed for one year.
- **Lleida Post-COVID**: later waves, followed for up to 4 years.
- **Other cohorts**: Tenacity (various viral infections) and Virgen del Rocío (short term), used to test whether the phenotypes extend to other diseases and populations.

The idea is to find **reproducible phenotypes** at an early stage and use them to predict long-term outcomes. The temporal design is:

| Phenotyping at | Trajectory followed in CIBERES | Long-term follow-up (Lleida) |
|---|---|---|
| 3 months | 6 months → 12 months | up to 4 years |
| 6 months | 12 months | up to 4 years |
| 12 months | – | behaviour in Lleida |

For each time point we cluster patients using their symptoms, functional tests (e.g. DLCO, TLC, FVC), radiological findings and clinical data. We then study how each cluster evolves at later visits. Finally, we check whether the longer-follow-up Lleida patients fit into the same groups, so that long-term sequelae can be anticipated from early data.

## Pipeline

1. **Exploratory analysis** (`01_analisis_exploratorio.ipynb`): structure, missingness and distributions.
2. **Cleaning and unification** (`02_limpieza.ipynb`): a unified cohort (full and core versions) with a variable dictionary.
3. **CIBERES phenotyping** (`03_fenotipado_ciberes.ipynb`): clustering at 3m, 6m and 12m.
4. **Lleida phenotyping** (`04_fenotipado_lleida.ipynb`): projection of Lleida patients onto the phenotypes and long-term follow-up.
5. **Common phenotyping** (`05_fenotipado_comun.ipynb`): a shared phenotype space across cohorts.
6. **Interpretation and visualisation**: cluster profiles, defining variables and recovery trajectories, in a form that clinicians can read.

## Repository structure

```
respira-hackathon/
├── Workflow/        # Workflow of the project
├── src/             # Source code (clustering, tables, visualisation)
├── .gitignore       # Excludes data and temporary files
├── config.yaml      # Pipeline configuration
├── main.ipynb       # Main end-to-end notebook
└── README.md
```

## Getting started

```bash
git clone [https://github.com/carlospalazon/respira-hackathon.git](https://github.com/carlospalazon/respira-hackathon.git)
cd respira-hackathon
pip install -r requirements.txt   # if available
jupyter notebook main.ipynb
```

Edit `config.yaml` to set data paths and clustering parameters. Patient data is **not** included in the repository for privacy reasons.

## Key features

- **Reproducible**: configuration-driven pipeline, so the same method applies to other cohorts.
- **Interpretable**: each phenotype is described by its defining variables.
- **Longitudinal**: trajectories at 3, 6, 12 months and up to 4 years.
- **Transferable**: designed to extend beyond COVID-19 to other respiratory infections.

## Results

See [`Informe.md`](Informe.md) for the full methodology, clustering results and clinical interpretation of the phenotypes.

## Team

Developed during the Respira Hackathon by:

- Nil Muriach
- Carlos Palazón
- Ferran Òdena

## Acknowledgements

We thank CIBER and its respiratory research area, CIBERES, as well as AstraZeneca, for making the Respira Hackathon possible.

We also thank the challenge leads, clinicians, researchers and mentors for their guidance, clinical insights and feedback throughout the event. Their support helped us connect the data-analysis work with the clinical questions behind the challenge.


