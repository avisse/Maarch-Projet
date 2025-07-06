# 📁 Maarch-Projet – Déploiement et CI/CD

Projet DevOps personnel centré sur le **déploiement de Maarch Courrier via Docker**, avec **automatisation** et **pipeline CI/CD GitHub Actions**.

## 🎯 Objectifs

- Déployer l'application **Maarch Courrier (v2301)** dans un environnement isolé via **Docker Compose**
- Créer un **conteneur PostgreSQL** configuré pour la base de données de Maarch
- Gérer les connexions inter-conteneurs via un **réseau Docker personnalisé**
- Rendre la plateforme accessible via navigateur (port 8080)
- Assurer la **persistance des données** avec des volumes Docker
- Mettre en place une **pipeline CI/CD GitHub Actions** (étape expérimentale)

---

## ⚙️ Technologies utilisées

- **Docker & Docker Compose**
- **PostgreSQL 14**
- **Maarch Courrier (image officielle)**
- **Git + GitHub**
- **GitHub Actions** (pipeline CI/CD)
- **Shell script (start.sh)**

---

## 📂 Structure du dépôt

├── .github/workflows/
│ └── ci.yml # (pipeline GitHub Actions)
├── docker-compose.yml # Définition des services Docker
├── start.sh # Script shell de démarrage
└── README.md # Documentation du projet

yaml
Copier
Modifier

---

## 🚀 Lancement du projet

1. **Cloner le dépôt** :
```bash
git clone https://github.com/avisse/Maarch-Projet.git
cd Maarch-Projet
Lancer les conteneurs :

bash
Copier
Modifier
docker-compose up -d
Accéder à Maarch Courrier :
Ouvrir le navigateur sur http://localhost:8080

Identifiants par défaut à définir dans l’image Maarch.

🐘 Configuration PostgreSQL
Le service maarch_db expose une base PostgreSQL avec :

Utilisateur : maarch

Mot de passe : maarch

Base de données : maarchcourrier

Le fichier postgresql.conf est modifié pour permettre la connexion à distance via listen_addresses = '*'.

🛠 Problèmes résolus
❌ Connexion impossible entre conteneurs → corrigé par l’ajout d’un réseau Docker commun (maarch_net)

❌ PHP display_errors désactivé → contourné via une modification dans php.ini

❌ Erreur de persistance → résolution par ajout de volumes Docker (maarch_pgdata, maarch_appdata)

🔁 CI/CD (GitHub Actions)
Une ébauche de pipeline CI/CD est incluse (.github/workflows/ci.yml).
Ce pipeline vise à :

Vérifier la syntaxe du docker-compose.yml

Simuler un déploiement

Statut actuel : expérimental – en cours d’amélioration.

💾 Volumes Docker
yaml
Copier
Modifier
volumes:
  maarch_pgdata:      # Données PostgreSQL persistantes
  maarch_appdata:     # Données applicatives de Maarch Courrier
✅ Résultat attendu
Maarch Courrier opérationnel à l'adresse http://localhost:8080

Données PostgreSQL persistées au redémarrage

Base relationnelle connectée automatiquement

📌 À venir
Ajout d’un script de sauvegarde PostgreSQL

Documentation avancée utilisateur

Optimisation du start.sh

