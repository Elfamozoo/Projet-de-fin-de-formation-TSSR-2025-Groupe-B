# Projet Final TSSR – Infrastructure PME

## 📌 Contexte
Une PME spécialisée dans la vente d’articles de sport ouvre ses portes.  
Elle a besoin d’une infrastructure informatique robuste, virtualisée et sécurisée, afin de répondre aux besoins de ses équipes internes et des agents nomades.  

Ce projet constitue le **projet de fin de formation TSSR**, avec pour objectifs :  
- Mettre en place une infrastructure virtualisée hautement disponible.  
- Fournir les services essentiels (AD, DNS, DHCP, GLPI, VoIP, supervision, messagerie…).  
- Sécuriser l’accès via un pare-feu pfSense et la segmentation VLAN.  
- Centraliser l’administration via **vCenter**.  
- Garantir la sauvegarde et la redondance des données avec un SAN iSCSI.  

---

## 🖥️ Schéma d’architecture
![Topologie Réseau](Docs/Diagrammes/Diagramme%20Topologie.png)

---

## 🌐 Plan d’adressage
| VLAN  | Usage               | Réseau        | Passerelle (SVI) | Notes |
|-------|---------------------|---------------|------------------|-------|
| 10    | Serveurs            | 10.10.10.0/24 | 10.10.10.1       | AD, DNS, DHCP, Fichiers, MDM, CMS, FTP, GLPI, Supervision |
| 20    | Clients             | 10.10.20.0/24 | 10.10.20.1       | Postes utilisateurs & nomades |
| 30    | Connexion WAN       | 10.10.30.0/24 | 10.10.30.1       | Sortie Internet via pfSense |
| 99    | Infra Physique      | 10.10.99.0/24 | 10.10.99.1       | ESXi, SAN, VCSA |

---

## 🛠️ Services déployés
### Windows
- **SRV-AD01** : Active Directory, DNS, DHCP, Serveur de fichiers  
- **SRV-MDM** : ManageEngine Mobile Device Manager Plus  

### Linux
- **SRV-LX01** : CMS (HTTP/HTTPS), FTP(s)  
- **SRV-LX02** : GLPI & Supervision (Zabbix)  
- **SRV-LX03** : VoIP & Syslog (prévu)  
- **SRV-LX04** : Serveur de messagerie (Postfix, prévu)  

### Autres équipements
- **pfSense** : Pare-feu, Proxy, VPN Nomade  
- **Switch L3 Cisco** : Routage inter-VLAN  
- **SAN iSCSI** : Stockage VMDATA et ISO  
- **vCenter** : Gestion centralisée des hyperviseurs ESXi  

---

## 📂 Organisation du repository
```
TSSR-Projet-Final/
│
├── docs/              → Cahier des charges, schémas, procédures
├── config/            → Configs Switch L3, pfSense, VMware
├── scripts/           → Scripts de déploiement/administration
├── livrables/         → Rapport final, slides soutenance
└── tests/             → Résultats de tests & captures
```

---

## 👥 Équipe & rôles
- **Administrateur Système** → Gestion AD, DHCP, fichiers, MDM  
- **Administrateur Réseau** → Switch L3, VLANs, pfSense, routage  
- **Administrateur Virtualisation** → ESXi, vCenter, SAN  
- **Responsable Applicatifs** → GLPI, Supervision, CMS, VoIP, Mail  

---

## 🎯 Livrables attendus
- Rapport final documenté (PDF)  
- Présentation PowerPoint (soutenance)  
- Procédures techniques (Word/Markdown)  
- Configurations (Switch, pfSense, VM)  

---

## 📅 Deadline
- Soutenance orale prévue le **02 octobre 2025**.  
