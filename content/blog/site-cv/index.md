---
title: "Site CV — Hugo + Terraform + Azure"
date: 2026-10-21
tags: ["hugo", "terraform", "azure", "github-actions"]
draft: false
---

## Le projet

Ce site est un **démonstrateur complet d'infrastructure as code** : une vitrine pour montrer que je sais non seulement administrer des systèmes, mais aussi **industrialiser un déploiement** de bout en bout.

## La stack

| Brique | Rôle |
|---|---|
| **Hugo** | Génération du site statique (CV, projets, blog) |
| **GitHub Actions** | CI/CD : build + déploiement automatique à chaque push |
| **Azure Static Web Apps** | Hébergement (free tier, HTTPS, domaine custom) |
| **Terraform** | Provisionnement de l'infrastructure Azure en code |
| **Git** | Versioning + historique du projet |

## Pourquoi cette stack

- **Hugo** : générateur statique ultra-rapide, contenu en markdown, pas de base de données — parfait pour un CV.
- **Terraform** : l'infrastructure est décrite dans un fichier reproductible. On peut détruire et recréer l'environnement à l'identique en une commande.
- **Azure Static Web Apps** : hébergement managé avec free tier généreux et CI/CD intégré à GitHub.
- **GitHub Actions** : à chaque `git push`, le workflow build le site et le déploie — plus d'action manuelle.

## Le parcours du code

1. `git push` vers GitHub
2. Le workflow Actions récupère le dépôt (+ le thème en submodule)
3. Installation de Hugo + `npm install` (Tailwind CSS v4)
4. `hugo --gc` génère le site dans `public/`
5. Azure Static Web Apps reçoit le dossier et sert le site

## Ce que ça prouve

- ✅ Infrastructure as Code (Terraform)
- ✅ CI/CD (GitHub Actions)
- ✅ Conteneurisation / workflows modernes (Hugo + Tailwind + Node)
- ✅ Bonnes pratiques Git (branches, submodules, versioning)

## Remarque technique

Le thème (aafu) est ajouté en **submodule git** et son contenu de démonstration doit être purgé avant chaque build — d'où la commande de nettoyage dans le workflow (`rm -rf themes/aafu/content/blog/markdown_syntax ...`).