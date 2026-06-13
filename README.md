#  Network Labs — Travaux Pratiques en Sécurité et Administration Réseau

> Ensemble de Labs pratiques réalisés en cours d'ingénierie cybersécurité.  
> Les travaux couvrent la configuration réseau, le routage, la sécurité périmétrique et la cryptographie, à travers des simulations Cisco Packet Tracer et des environnements Linux virtualisés.

---

##  Compétences mises en œuvre

| Domaine | Technologies & Protocoles |
|---|---|
| **Routage** | RIPv1, RIPv2, OSPF mono/multi-aires, routage statique IPv4/IPv6 |
| **Sécurité réseau** | ACL standard/étendue, pare-feu Cisco ASA, DMZ, IPsec VPN Site-to-Site |
| **Cryptographie** | SHA-1, DES-CBC, RSA 2048 bits, OpenSSL |
| **Analyse réseau** | Nmap, reconnaissance passive/active, scan de ports |
| **Adressage** | IPv4, IPv6 (global unicast, link-local), VLAN, NAT/PAT |
| **Virtualisation** | Oracle VirtualBox, routage inter-VM, configuration Linux |
| **Outils** | Cisco Packet Tracer, Kali Linux, OpenSSL, Nmap |

---

## 📁 Contenu du dépôt

### 🔵 `Advanced_Company_Network.pkt` — Simulation réseau d'entreprise avancée
**Fichier Cisco Packet Tracer**

-> Infrastructure & Haute Disponibilité : Mise en place d'un design hiérarchique avec routage OSPF pour l'interconnexion, couplé à du HSRP et du LACP (EtherChannel) pour éviter les points de défaillance unique.

-> Sécurité & Segmentation : Utilisation de firewalls Cisco ASA avec des zones dédiées (Inside/Outside/DMZ). J'ai configuré des ACLs pour le filtrage et sécurisé les accès distants via SSH. Côté accès, j'ai activé le PortFast et le BPDUGuard pour verrouiller les ports commutés.

-> Services : Gestion centralisée du WiFi via un contrôleur WLC, déploiement d'une solution de téléphonie IP (Voice Gateways & IP Phones) et centralisation du DHCP via Active Directory.

**Compétences :** architecture réseau d'entreprise, configuration multi-équipements Cisco, intégration des protocoles de routage et de sécurité.

---

### 🔴 `Lab1 Network Scanning Nmap.pdf` — Reconnaissance réseau avec Nmap
**Environnement :** Kali Linux + Metasploit (VirtualBox, réseau isolé `192.168.56.0/24`)

Simulation de la phase de reconnaissance d'un attaquant réel. Les différentes techniques de découverte réseau sont explorées et analysées :
- Utilisation de `nmap --traceroute` pour cartographier la topologie et identifier les équipements intermédiaires
- Scan de découverte d'hôtes (`-sn`), analyse des interfaces (`--iflist`)
- Comparaison des types de scan : **SYN scan**, **TCP connect scan**, **UDP scan**
- Concepts de **footprinting** passif (WHOIS, Shodan) et actif (ICMP, ARP)

**Compétences :** audit de sécurité réseau, analyse de la surface d'attaque, maîtrise de Nmap, connaissance des phases d'une cyberattaque.

---

### 🔴 `Lab 2 ACL.pdf` — ACL, NAT/PAT et Pare-feu ASA avec DMZ
**Environnement :** Cisco Packet Tracer

Rapport couvrant trois laboratoires de sécurité réseau :

**Partie 1 — Listes de Contrôle d'Accès (ACL)**
- Configuration d'ACL **standard** (filtrage par source IP) et **étendue** (filtrage par protocole, port, source/destination)
- Application sur des interfaces Cisco, vérification des règles via `show access-lists`
- Tests de connectivité avant/après application pour valider le filtrage

**Partie 2 — NAT et PAT**
- NAT statique (1:1), NAT dynamique (pool d'adresses), PAT (surcharge d'adresse)
- Mise en place de la translation pour permettre la communication réseau privé ↔ public

**Partie 3 — Pare-feu Cisco ASA 5505 avec DMZ**
- Segmentation en trois zones : `Inside` (security-level 100), `DMZ` (security-level 70), `Outside` (security-level 0)
- Configuration des VLANs, routage statique, règles NAT et ACL sur le pare-feu

**Compétences :** filtrage réseau, sécurité périmétrique, translation d'adresses, architecture DMZ.

---

### 🔴 `Lab 5 _ cryptography.pdf` — Cryptographie appliquée avec OpenSSL
**Environnement :** Linux, OpenSSL

Exploration pratique des fondamentaux de la cryptographie :

- **Fonctions de hachage :** génération et comparaison d'empreintes SHA-1 sur des fichiers modifiés (`openssl dgst -sha1`)
- **Chiffrement symétrique :** chiffrement et déchiffrement d'un fichier avec l'algorithme **DES-CBC**, encodage Base64, gestion des clés partagées
- **Chiffrement asymétrique RSA :**
  - Génération d'une paire de clés RSA 2048 bits (`privMyName.key`)
  - Extraction de la clé publique (`pubMyName.key`)
  - Chiffrement d'un fichier avec la clé publique, déchiffrement avec la clé privée
  - Vérification de l'intégrité par comparaison (`diff`)

**Compétences :** cryptographie symétrique/asymétrique, PKI, OpenSSL, intégrité des données.

---

### 🔴 `Lab 6 IPsec VPN.pdf` — VPN Site-à-Site IPsec
**Environnement :** Cisco Packet Tracer (3 routeurs)

Mise en place d'un tunnel VPN chiffré entre deux sites distants (R1 ↔ R3) :
- Configuration **ISAKMP Phase 1** : algorithme **AES-256**, hachage **SHA-1**, échange de clés **Diffie-Hellman groupe 5**, clé pré-partagée
- Définition du trafic intéressant via **ACL 110** (sélection des flux à chiffrer)
- Encapsulation **IPsec** sur l'interface série de sortie
- **Vérification du tunnel :** analyse des compteurs `#pkts encaps/encrypt/decaps/decrypt` via `show crypto ipsec sa`
- Validation de la sélectivité : seul le trafic ciblé est chiffré, le reste transite normalement

**Compétences :** VPN IPsec, protocoles de négociation IKE, chiffrement des communications inter-sites.

---

### 🔵 `Lab #–Configuring Basic RIPv2.pdf` — Configuration RIPv2 de base
**Environnement :** Cisco Packet Tracer (3 routeurs R1/R2/R3)

Mise en œuvre du protocole de routage dynamique à vecteur de distance RIPv2 sur une topologie WAN avec liaisons série. Configuration des interfaces, activation du processus RIP, vérification des tables de routage et tests de connectivité bout-en-bout.

**Compétences :** routage dynamique, protocoles à vecteur de distance, convergence réseau.

---

### 🔵 `TP RIPv1-v2_OSPF.pdf` — Routage dynamique : RIPv1, RIPv2 et OSPF
**Environnement :** Cisco Packet Tracer

Progression complète du routage statique vers le routage dynamique en trois étapes :

1. **RIPv1** — Configuration de base, validation par ping entre tous les hôtes du réseau
2. **RIPv2** — Migration vers le routage sans classe (CIDR), injection et redistribution d'une route par défaut (simulation accès Internet)
3. **OSPF mono et multi-aires :**
   - Déploiement en **Area 0**, vérification des adjacences FULL
   - Architecture multi-aires avec configuration des **ABR** (Routeurs Frontières d'Aire), propagation des routes inter-aires (`O IA`)
   - **Sécurisation par authentification MD5** sur les échanges OSPF
   - Optimisation via `area range` (résumé de routes, réduction des LSDB)

**Compétences :** protocoles de routage dynamique, OSPF multi-aires, sécurisation des protocoles, optimisation des tables de routage.

---

### 🔵 `TP Conf routeur Add Ipv6.pdf` — Routage statique IPv4 & Configuration IPv6
**Environnement :** Cisco Packet Tracer

Deux travaux pratiques complémentaires :

- **TP2 — Routage statique IPv4 :** configuration de deux routeurs interconnectés via un lien série, ajout de routes statiques pour permettre la communication entre PC0 et PC1 sur des sous-réseaux distincts, validation par `show ip int brief` et ping
- **TP3 — Adressage IPv6 :** configuration des interfaces avec adresses IPv6 globales et link-local, activation du routage IPv6, tests de connectivité et vérification des tables de routage

**Compétences :** routage statique, configuration IPv4/IPv6 sur Cisco IOS, dépannage réseau.

---

### 🔵 `TP ipv6.pdf` — Réseau IPv6 : configuration et validation
**Environnement :** Cisco Packet Tracer (R1, switch, PC-A, PC-B)

- Configuration d'adresses **IPv6 globales** et **link-local** (`FE80::1`) sur les interfaces du routeur R1
- Validation de la connectivité bout-en-bout par `ping` et `tracert` entre PC-A et PC-B via R1
- Compréhension du scope des adresses link-local (non routables, locales au lien)
- Analyse du comportement ICMPv6 (paquets envoyés uniquement au lien local)

**Compétences :** adressage IPv6, protocole ICMPv6, configuration de routeur Cisco, diagnostic réseau.

---

### 🔵 `TP4--Parefeu DMZ-INTER.pdf` — Pare-feu Cisco ASA 5505 : zones Inside/Outside/DMZ
**Environnement :** Cisco Packet Tracer

Configuration approfondie d'un pare-feu Cisco ASA 5505 :
- Assignation des ports Ethernet aux **VLANs** (VLAN 1 Inside, VLAN 2 Outside, VLAN 3 DMZ)
- Définition des **niveaux de sécurité** par interface pour contrôler la direction des flux
- Route statique par défaut (`0.0.0.0/0`) pointant vers le routeur R1 comme passerelle de dernier recours
- Configuration NAT/PAT pour l'accès Internet depuis le réseau interne
- **NAT statique** pour exposer le serveur DMZ depuis Internet
- **ACL** autorisant l'accès au serveur DMZ uniquement depuis l'extérieur
- Commande `no forward interface vlan 1` pour isoler strictement la DMZ du réseau interne

**Compétences :** pare-feu next-generation, architecture de sécurité en zones, NAT avancé, politique de contrôle d'accès.

---

### 🔵 `Lab8 Virtualization.pdf` — Virtualisation et routage Linux
**Environnement :** Oracle VM VirtualBox, Linux Ubuntu

Configuration d'une infrastructure réseau virtualisée composée d'un PC Router Linux et de plusieurs VMs réparties sur trois sous-réseaux :
- Configuration statique de trois interfaces réseau (`eth0/eth1/eth2`) via `/etc/network/interfaces`
- Architecture segmentée : `192.168.11.0/24`, `192.168.22.0/24`, `192.168.33.0/24`
- Analyse des tables de routage (`route -n`) et vérification de la connectivité inter-sous-réseaux
- Commandes Linux réseau : `ifconfig`, `route`, `ping`

**Compétences :** virtualisation réseau, Linux networking, segmentation d'infrastructures, configuration multi-interfaces.

---

##  Environnements et outils utilisés

- **Cisco Packet Tracer** — Simulation de topologies réseau Cisco (routeurs, switches, ASA)
- **Kali Linux** — Environnement d'audit et de test d'intrusion
- **Oracle VM VirtualBox** — Virtualisation de machines Linux en réseau isolé
- **OpenSSL** — Opérations cryptographiques (hachage, chiffrement symétrique/asymétrique)
- **Nmap** — Scanner de réseau et outil de découverte

