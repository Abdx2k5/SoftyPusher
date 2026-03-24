# SoftyPusher 🚀
> **Automated Web Delivery Engine — by SoftyGroup**

SoftyPusher est le moteur de delivery automatisé de **SoftyService**. Il transforme un brief client en site web livrable, testé et documenté via un pipeline de 9 agents IA orchestrés sur **n8n**, entièrement en local, sans coût cloud.

---

## 🎯 Vision

Les petits commerces (coworking, padel, cafés, salles de sport, hammam, studios...) gèrent encore leurs réservations sur WhatsApp. SoftyPusher leur livre un site complet avec système de réservation en **moins de 5 jours ouvrés** — packagé, testé, documenté.

> *"Fini les réservations sur WhatsApp à minuit — vos clients réservent et paient seuls 24h/24."*

---

## 🏗️ Architecture — Pipeline 9 agents

```
[Brief Client]
      │
      ▼
┌─────────────┐
│ 01 Discovery│ ──► Comprend le besoin, génère le brief structuré (JSON)
└─────────────┘
      │
      ▼
┌─────────────┐
│ 02 Design   │ ──► Sélectionne la maquette depuis la bibliothèque GitHub
└─────────────┘
      │
      ▼
┌─────────────┐
│ 03 Architect│ ──► Définit l'architecture, instruite les agents Dev
└─────────────┘
      │
      ├────────────────────┐
      ▼                    ▼
┌──────────────┐   ┌──────────────┐
│ 04 Frontend  │   │ 05 Backend   │
│ Dev          │   │ Dev          │
└──────────────┘   └──────────────┘
      │                    │
      └────────┬───────────┘
               ▼
┌──────────────────┐
│ 06 Agile / GitHub│ ──► Tickets, branches, PRs, releases
└──────────────────┘
               │
               ▼
┌──────────────────┐
│ 07 CI/CD         │ ──► Build, lint, déploiement automatique
└──────────────────┘
               │
      ┌────────┴────────┐
      ▼                 ▼
┌───────────┐   ┌────────────────┐
│ 08 Tester │   │ 09 Tester Sécu │
│ QA        │   │ (OWASP)        │
└───────────┘   └────────────────┘
               │
               ▼
      ✅ Validation humaine → Livraison client
```

---

## 🏪 Verticals ciblés

| Vertical | Besoin principal |
|---|---|
| 🏸 Padel / Sport | Réservation terrains + créneaux |
| ☕ Café / Lounge | Réservation salles privatisables |
| 💼 Coworking | Bureaux, hot-desk, abonnements |
| 💆 Hammam / Spa / Beauté | Prise de RDV en ligne |
| 💪 Salle de sport | Inscriptions cours + abonnements |
| 📸 Studio photo / créatif | Réservation créneaux + matériel |
| 🎉 Salle des fêtes | Disponibilités + devis automatique |
| 🎓 Centre de formation | Inscriptions + suivi stagiaires |
| 🛒 E-commerce local | Boutique + catalogue IA + admin |

---

## 🛠️ Stack technique

| Composant | Technologie |
|---|---|
| Orchestration | n8n (self-hosted, offline) |
| Modèles IA | Ollama + LLMs locaux (Mistral, CodeLlama) |
| Base templates | Repos GitHub open source par vertical |
| Frontend | React / Next.js + Tailwind CSS |
| Backend | Node.js / FastAPI |
| Base de données | PostgreSQL / Supabase |
| CI/CD | GitHub Actions (auto-généré par agent) |
| Tests | Playwright (E2E) + Jest (unit) |
| Paiement | Stripe / CMI Maroc |

---

## 💰 Pricing

### 🇲🇦 Marché Maroc — Portfolio & références
| Offre | Prix | MCO |
|---|---|---|
| SiteSprint Starter | 4 000 – 6 000 MAD | 400 – 600 MAD/mois |
| SiteSprint Pro | 7 000 – 12 000 MAD | 700 – 1 000 MAD/mois |
| SiteSprint E-commerce | 8 000 – 15 000 MAD | 800 – 1 200 MAD/mois |

### 🇫🇷 Marché France — Revenu principal
| Offre | Prix | MCO |
|---|---|---|
| SiteSprint Starter | 1 500 – 2 500 € | 150 – 200 €/mois |
| SiteSprint Pro | 3 000 – 4 500 € | 250 – 350 €/mois |
| SiteSprint Premium | 5 000 – 8 000 € | 400 – 600 €/mois |
| SiteSprint E-commerce IA | 4 000 – 7 000 € | 350 – 500 €/mois |

---

## 🗺️ Roadmap

```
Phase 0 (M0 → M2)  ── Setup n8n + Ollama + bibliothèque GitHub
Phase 1 (M2 → M4)  ── Validation pipeline sur projet fictif
Phase 2 (M4 → M6)  ── 3-5 premiers clients Maroc + case studies
Phase 3 (M6 → M12) ── Scale 3-5 sites/mois + 1er client France
Phase 4 (M12 → M24)── Intégration SoftyService + Afrique de l'Ouest
```

---

## ⚙️ Installation (Setup local)

### Prérequis
- Windows 10/11 — 16 GB RAM minimum
- [Docker Desktop](https://www.docker.com/products/docker-desktop)
- [Ollama](https://ollama.com/download)

### 1. Lancer n8n
```powershell
docker volume create n8n_data

docker run -d --name n8n -p 5678:5678 \
  -v n8n_data:/home/node/.n8n \
  --restart unless-stopped \
  n8nio/n8n
```
Accès : **http://localhost:5678**

### 2. Installer les modèles IA
```powershell
ollama pull mistral
ollama pull codellama
```

### 3. Connecter Ollama à n8n
Dans n8n → Settings → Community Nodes :
```
n8n-nodes-ollama
```
Credential Ollama URL : `http://host.docker.internal:11434`

---

## 📊 KPIs cibles

| KPI | Cible M6 | Cible M12 |
|---|---|---|
| Temps de livraison / site | <= 5 jours | <= 3 jours |
| Marge brute / projet | >= 75% | >= 85% |
| Contrats MCO actifs | 5+ | 15+ |
| CA récurrent | >= 30% | >= 50% |
| Sites livrés | 8-10 | 30+ |

---

## 🏢 Positionnement SoftyGroup

```
SoftyHolding (stratégie, marque, IP)
├── SoftyService  ◄── SoftyPusher est le moteur de delivery
└── SoftyBusiness ◄── Vend les offres SiteSprint, gère les clients
```

---

## 📄 License & Confidentialité

Document interne confidentiel — SoftyGroup © 2026.  
Tous droits réservés. Ne pas distribuer sans autorisation.

---

*Built with 🤖 by SoftyGroup — Maroc & Afrique de l'Ouest*
