---
title: "ETHaP 2025 - Atelier 3 - Initiation à XForms"
author: "Emmanuel Château-Dutier ; Josselin Morvan"
date: "2025-09-30"
---

# ETHaP 2025 - Atelier 3 - Initiation à XForms

## Présentation XForms
@emchateau ?

---

## Hello XForms!

---
### Objectifs

- Déployer une application XForms simple et maîtriser l'architecture MVC (*Modèle Vue Contrôleur*)
  - déclarer une instance XML ;
  - interagir avec le modèle de données ;
  - contrôler et valider ses données ;
  - enregistrer ses données ;

- Comment ?
  - ensemble ;)
  - un formulaire pour la saisie des données d'un carnet d'adresses

--- 
### Prérequis

- connaissance des langages xHTML, XPath et XML (TEI) ;
- télécharger l'archive [ethap2025-atelier3-xforms.zip](https://github.com/sardinecan/ethap2025-atelier3-xforms/archive/refs/heads/main.zip) 
- disposer d'un serveur local capable de servir des documents HTML ou XML ;

---
### Installation

Pour cette leçon nous utiliserons BaseX pour servir nos documents XForms.

- Décompresser l'archive `ethap2025-atelier3-xforms.zip` dans le répertoire `static` de BaseX
  - `chemin/vers/basex/webapp/static/`
- Lancer BaseX et ouvrir le navigateur web à l'adresse [http://localhost/static/ethap2025-atelier3-xforms/](http://localhost/ethap2025-atelier3-xforms/)

---
### L'architecture MVC de XForms

Un document XForms est un document XHTML avec :

- un modèle (<xf:model>), placé dans l'en-tête contenant les instances de données (<xf:instance>) ;
- un ensemble de contrôles, champs de formulaire, etc. placés dans le corps du document.

L'ensemble doit être servi comment un document XML (extension `.xml` ou `.xhtml`).

---
### Le modèle de données

- Quelles informations trouve-t-on dans un carnet d'adresses ?

<!--
    Quelles données trouve-t-on dans un carnet d'adresses ?
    - nom
    - date naissance
    - adresse -> faire un champ unique type zone de texte ou addrLine répétable (long si déjà les téléphones et emails) -> addrLine[1]
        - rue
        - code postal
        - ville
    - téléphone -> sûr qu'on aura les deux ? -> approche agnostique @type ! 
        - mobile
        - fixe
    - email -> plusieurs emails ?
-->

- Comment les représenter en XML…

<!-- 
    ouvrir un éditeur de texte et modéliser les données
    - quels éléments ?
    - certains éléments devront-ils être répétés ?
-->

- et en TEI ?
<!-- 
    Proposer une modélisation en TEI <listPerson>, <person>, etc.
    l'intégrer dans le XForms
-->

---
### Interagir avec ses données - les contrôles simples

XForms propose plusieurs types de champs (`controls`) pour interagir avec les données

- champs texte (`<xf:input/>`) ;
- zones de texte (`<xf:textarea/>`) ;
- listes à choix unique (`<xf:select1/>`) ;
- cases à cocher (`<xf:select/>`) ;
- bouton (`<xf:trigger/>`)
- groupe (`<xf:group/>`)

Ces contrôles sont reliés à notre modèle de données par l'intermédiaire d'un attribut `@ref` contenant un chemin *XPath*.
<!--
    - Faire le champ nom ensemble
    - faire un output serialize pour montrer la magie XForms
    - les laisser faire avec date naissance et l'adresse avec addrLine[1]
    - puis blocage avec les téléphones 
-->

---

### Interagir avec ses données - les séquences d'éléments

Lorsque l'on a une séquence indéterminée d'élément, 
