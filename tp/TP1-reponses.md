# TP1 — Cadrage du projet : Location de voitures

**Équipe :** Moemen Riahi, Moenes Azzi, Yassine Ben Youssef, May Slema


## 1. Vision

### Q1. Formulez le problème métier en une seule phrase, sans citer de technologie. Quelle phrase de la demande décrit déjà une solution plutôt que le problème ?

* **Formulation du problème métier :**  
  La gestion actuelle des réservations de véhicules ne permet pas à l’agence de consulter facilement les disponibilités et peut entraîner des conflits de réservation.

* **Phrase décrivant une solution plutôt que le problème :**  
   « Notre agence souhaite une plateforme en ligne pour louer nos voitures. »

---

### Q2. Listez les parties prenantes (explicites et potentielles/impactées) avec leurs attentes vis-à-vis du projet.

| Partie prenante | Statut | Attente / Intérêt vis-à-vis du projet |
| :--- | :--- | :--- |
| **Client (locataire)** | Explicite | Visualiser les voitures disponibles en temps réel, réserver en ligne en toute autonomie et connaître immédiatement le coût exact. |
| **Agent de comptoir (3)** | Explicite | Gérer les réservations et le parc au guichet ; remettre en location les voitures le plus rapidement possible pour maximiser l'activité. |
| **Préparateur (2)** | Explicite | Disposer d'un créneau garanti et suffisant entre deux locations pour inspecter et nettoyer chaque voiture. |
| **Responsable d'agence (1)** | Explicite | Disposer d'une visibilité globale sur l'activité, la rotation du parc automobile et la rentabilité de l'agence. |
| **Conducteur additionnel** | Potentielle | Être pris en compte sur le contrat de location et voir son éligibilité (âge/permis) vérifiée sans friction. |
| **Service comptable / facturation** | Potentielle | Automatiser l'encaissement, la gestion des cautions/dépôts de garantie et la facturation des pénalités de retard. |

---

### Q3. Formulez au moins 2 objectifs avec le gabarit SMART (en conservant les valeurs inconnues sous la forme `[à valider]`).

* **OBJ-01 :** Réduire le temps moyen nécessaire à un client pour trouver un véhicule disponible et finaliser sa réservation avec affichage du prix ferme de **[valeur actuelle à mesurer]** à **[valeur cible à valider]** d'ici **[délai à valider]** après la mise en service.
* **OBJ-02 :** Réduire le taux de retards de restitution non régularisés ou sans pénalité appliquée de **[valeur actuelle à mesurer]** à **[valeur cible à valider]** au cours de **[période à valider]**.
* **OBJ-03 :** Garantir un délai effectif de nettoyage entre deux clients successifs pour **[proportion à valider]** des rotations de véhicules dans un délai de **[délai à valider]**.
**OBJ-04 :** Améliorer la précision du calcul des prix de location en augmentant le pourcentage de locations dont le prix est correctement calculé automatiquement de [valeur actuelle à mesurer] à [valeur cible à valider] dans un délai de [à valider].



---

### Q4. Parmi les objectifs du client, lequel vous semble le plus difficile à mesurer ? Pourquoi ?

* **Objectif le plus difficile à mesurer :**  
  Proposer un tarif intéressant pour les longues locations.
* **Pourquoi :**  
  La notion de tarif **« intéressant »** est subjective et ne précise aucun seuil de réduction ou de prix attendu. Il faut donc définir avec le client des critères chiffrés pour pouvoir évaluer cet objectif.

---

## 2. Périmètre

### Q5. Tableau de classification (Ce que l'on sait / Ce que l'on ne sait pas)

| Élément analysé | Catégorie | Justification / Source dans la demande |
| :--- | :--- | :--- |
| **Consulter les voitures disponibles et réserver** | Dans le périmètre | Explicitement demandé : *« voir les voitures disponibles, réserver une location »*. |
| **Calcul automatique et immédiat du prix** | Dans le périmètre | Explicitement demandé : *« connaître tout de suite le prix »*, *« calculé automatiquement et correctement »*. |
| **Gestion des réservations et du parc (agents)** | Dans le périmètre, à préciser | Explicite, mais le verbe « gérer » reste ambigu quant aux opérations exactes. |
| **Suivi d'activité (responsable)** | Dans le périmètre, à préciser | Explicite, mais les indicateurs de suivi (KPIs) ne sont pas spécifiés. |
| **Offre spéciale week-end pour les familles** | Règle / Dans le périmètre | Explicite (*« offre spéciale »*), mais les conditions d'éligibilité famille restent à préciser. |
| **Pénalisation des retards de restitution** | Règle / Dans le périmètre | Explicite (*« doivent être pénalisés »*), mais le mode de calcul de la pénalité reste à définir. |
| **Système sécurisé** | Contrainte / BNF à préciser | Explicite (*« Le système doit être sécurisé »*), normes de conformité et sécurité à cadrer. |
| **Système agréable à utiliser** | BNF / Qualité à préciser | Explicite, mais subjectif et non mesurable en l'état. |
| **Âge minimum pour louer un véhicule** | Point ouvert | Le client refuse les conducteurs *« trop jeunes »*, sans indiquer de valeur seuil. |
| **Palier et réduction « longue location »** | Point ouvert | Le texte veut un tarif *« intéressant »*, sans spécifier le nombre de jours minimum ni le barème. |
| **Durée du délai de nettoyage** | Point ouvert | Conflit interne : arbitrage requis entre le temps préparateur et la remise en location immédiate. |
| **Modalités de paiement de la réservation** | Point ouvert | La demande exige l'affichage immédiat du tarif sans préciser si le paiement se fait en ligne ou au comptoir. |
| **Répartition équitable des 12 voitures en 3 catégories** | Hypothèse | Hypothèse de travail (ex. 4 citadines, 4 berlines, 4 SUV) non affirmée par le texte. |
| **Présentation d'un permis de plus de 2 ans requise** | Hypothèse | Pratique courante supposée par l'équipe, nécessitant confirmation formelle du client. |

---

### Q6. Proposez un élément que vous placeriez hors périmètre, et justifiez-le à partir du texte. Si le texte ne permet pas de conclure, classez-le en point ouvert.

* **Hors périmètre :**  
  La prise en charge des grosses réparations mécaniques en atelier ainsi que la vente de véhicules d'occasion.
    
  *Justification :* La demande se focalise strictement sur la réservation, la tarification, le nettoyage courant et la rotation de 12 véhicules de location.
* **Point ouvert (élément frontière à ne pas exclure sans avis client) :**  
  Le *paiement bancaire en ligne immédiat*. On ne peut pas l'exclure unilatéralement car il conditionne le parcours de réservation en ligne, mais rien n'indique formellement s'il est requis ou si le règlement s'effectue au comptoir.

---

## 3. Exigences

### Q7. Tableau des premières exigences rédigées et traçabilité

#### A. Exigences fonctionnelles complémentaires
| ID | Exigence formelle | Type | Source dans la demande | Appréciation |
| :--- | :--- | :--- | :--- | :--- |
| **REQ-F-01** | Le système doit permettre à un client de consulter la liste des voitures disponibles sur une plage de dates sélectionnée. | F | *« Les clients doivent pouvoir voir les voitures disponibles... »* | Atomique, claire et vérifiable. |
| **REQ-F-02** | Le système doit permettre à un client de réserver un véhicule disponible pour une période définie. | F | *« ...réserver une location... »* | Conforme et directement traçable. |
| **REQ-F-03** | Le système doit calculer et afficher immédiatement le montant total de la location en fonction de la catégorie, de la durée et des réductions applicables. | F | *« ...connaître tout de suite le prix »* / *« calculé automatiquement et correctement »* | Règle fonctionnelle clé. |
| **REQ-F-04** | Le système doit bloquer la réservation si l'âge du conducteur principal est inférieur à l'âge limite minimum `[âge à valider]`. | F | *« Nous ne voulons pas louer à des conducteurs trop jeunes... »* | Règle bloquante avec paramètre à valider. |
| **REQ-F-05** | Le système doit insérer automatiquement un intervalle d'indisponibilité pour nettoyage `[durée à valider]` à la suite de chaque restitution avant de rendre le véhicule disponible. | F | *« Les préparateurs demandent du temps pour nettoyer chaque voiture entre deux clients. »* | Répond fonctionnellement à la contrainte de préparation. |
| **REQ-F-06** | Le système doit appliquer une majoration financière `[barème à valider]` lors de la restitution d'un véhicule au-delà de l'horaire contractuel. | F | *« ...les clients qui rendent la voiture en retard doivent être pénalisés. »* | Traçable et vérifiable. |
| **REQ-F-07** | Le système doit appliquer un tarif avantageux aux locations dont la durée atteint le seuil de longue location [seuil à valider]. | F | « ...rester intéressant pour les longues locations. » | Le seuil et le barème de réduction sont à valider avec le client. |
| **REQ-F-08** | Le système doit appliquer l'offre spéciale week-end aux locations destinées aux familles [conditions à valider]. | F | « Le week-end, nous voulons attirer les familles avec une offre spéciale. » | La définition de « famille » et les conditions de l'offre restent à préciser. |
| **REQ-F-09** | Le système doit permettre à un agent de comptoir de gérer les réservations [opérations à valider]. | F | « Les agents du comptoir doivent gérer les réservations... » | Le terme « gérer » est ambigu : création, modification ou annulation des réservations. |
| **REQ-F-10** | Le système doit permettre à un agent de comptoir de gérer le parc automobile [opérations à valider]. | F | « ...et le parc automobile. » | Les opérations autorisées restent à préciser : ajout, retrait, déclaration d'indisponibilité, etc. |
| **REQ-F-11** | Le système doit permettre au responsable de suivre l'activité de l'agence [indicateurs à valider]. | F | « Le responsable veut suivre l'activité de l'agence. » | Les indicateurs de suivi (locations, revenus, disponibilité des véhicules, etc.) restent à définir. |
#### B. Exigence non fonctionnelle complémentaire
| **REQ-NF-01** | Le système doit être accessible et permettre à un utilisateur novice de finaliser une réservation en moins de `[durée à valider]`. | NF | *« Le système doit être [...] agréable à utiliser. »* | Rend mesurable le critère d'agrément. |
| **REQ-NF-02** | Le système doit protéger les données personnelles des conducteurs et chiffrer les transactions conformément aux normes en vigueur. | NF | *« Le système doit être sécurisé... »* | Cadrage de l'exigence de sécurité. |
| **REQ-NF-03** | Le système doit afficher le prix de la location dans un délai de [durée à valider] après la demande du client. | NF | « ...connaître tout de suite le prix. » | Rend mesurable l'expression « tout de suite » sans inventer de valeur cible. |

---

### Q8. Critique d'exigences et corrections

#### 1. Critique de : « Le système doit permettre aux agents de gérer le parc automobile. »
* **Problème :** Le verbe « gérer » est ambigu et englobant. Il ne précise pas quelles opérations sont permises (ajouter un véhicule, modifier un kilométrage, déclarer une panne, changer la catégorie, etc.).
* **Action / Correction :** Transformer l'ambiguïté en point ouvert pour le client :  
  > *« Quelles opérations exactes les agents de comptoir doivent-ils effectuer sur le parc automobile (création/retrait de véhicule, signalement d'indisponibilité, mise à jour du statut d'entretien) ? »*

#### 2. Critique de : « L'application doit bloquer les conducteurs de moins de 25 ans avec une application mobile téléchargeable sur Google Play. »
* **Problèmes :**
  1. *Valeur inventée :* « 25 ans » ne figure pas dans le texte du client (*« trop jeunes »*).
  2. *Solution technique prématurée :* Imposer une « application mobile Android » restreint l'architecture sans validation, le client demandant une « plateforme en ligne ».
* **Correction attendue :**  
  > *REQ-F-04 bis : Le système doit empêcher la confirmation d'une réservation si l'âge du conducteur principal est inférieur à l'âge minimum requis `[âge à valider]`.*

#### 3. « Le système doit pénaliser de 10 € par heure les clients qui rendent la voiture en retard. »

**Problèmes :**
- **Valeur inventée :** Le montant de 10 € par heure ne figure pas dans la demande du client.
- **Retard non défini :** Aucune marge de tolérance n'est précisée.
- **Mode de calcul supposé :** La pénalité horaire est imposée sans confirmation du client (forfait fixe, taux horaire ou journée supplémentaire).

**Correction :**

 *Le système doit appliquer une pénalité [barème à valider] à un client qui rend la voiture en retard.*

**Points ouverts à poser au client :**
- À partir de combien de minutes de retard une pénalité doit-elle être appliquée ?
- Quel mode de calcul faut-il utiliser (montant fixe, tarif horaire ou journée supplémentaire) ?

#### 4. « Le système doit calculer automatiquement le prix de la location et envoyer un e-mail de confirmation au client. »

**Problèmes :**
- **Deux idées dans une seule exigence :** Le calcul du prix et l'envoi d'un e-mail sont deux fonctionnalités distinctes.
- **Fonctionnalité non demandée :** L'envoi d'un e-mail de confirmation n'est pas explicitement mentionné dans la demande.
- **Extension non validée du périmètre :** Cette proposition ajoute une fonctionnalité sans accord préalable du client.

**Correction :**

- **Exigence 1 :** Le système doit calculer automatiquement le prix de la location.
- **Exigence 2 :** L'envoi d'un e-mail de confirmation doit rester un point ouvert à valider avec le client.

**Question à poser au client :**

Souhaitez-vous que les clients reçoivent une confirmation après leur réservation ? Si oui, par quel moyen (e-mail, SMS ou autre) ?

---

### Q9. Analyse de « simple / agréable à utiliser » et questions pour le rendre mesurable

* **Pourquoi ce n'est pas vérifiable en l'état :**  
  Le terme « agréable » est subjectif et non quantifiable. Un test de recette logiciel ne peut pas juger formellement si une interface est « agréable » sans indicateurs objectifs.
* **Questions à poser au client :**  
  1. Quel est le temps moyen maximum acceptable pour qu'un client effectue une réservation complète ?  
  2. En combien d'écrans ou d'étapes maximum le tunnel de réservation doit-il être découpé ?  
  3. Quel taux de succès minimal sans assistance attendez-vous lors des tests d'utilisabilité ?  
  4. L'application doit-elle satisfaire un niveau particulier de conformité ergonomique ou d'accessibilité (ex. WCAG / RGAA) ?
  5. Comment souhaitez-vous mesurer la satisfaction des utilisateurs (tests utilisateurs, questionnaire de satisfaction, taux d'abandon de réservation) ?
  6. Le système doit-il être utilisable sans formation préalable, notamment pour les agents de comptoir ?

---

## 4. Analyse IA

### Q10. Tableau de classement des propositions IA

| Proposition de l'IA | Décision | Justification (Preuve dans la demande) |
| :--- | :--- | :--- |
| **1. Préciser l'âge minimum d'éligibilité pour conduire un véhicule.** | **Acceptée** | Ambiguïté réelle directement issue de la demande : *« pas louer à des conducteurs trop jeunes »*. |
| **2. Exiger le versement d'une caution de 1 000 € par carte bancaire.** | **Rejetée comme exigence** | Montant et mécanisme de caution inventés par l'IA. Peut constituer un point ouvert, mais pas une exigence validée. |
| **3. Définir un temps incompressible pour le nettoyage entre deux réservations.** | **Acceptée** | Traduction indispensable du conflit opérationnel soulevé entre préparateurs et agents de comptoir. |
| **4. Développer une application native iOS/Android avec ouverture sans clé par Bluetooth.** | **Rejetée** | Solution technologique hors sujet et surspécifiée. La demande mentionne simplement une *« plateforme en ligne »*. |
| **5. Fixer le barème des pénalités de retard et une période de tolérance éventuelle.** | **Acceptée** | Précise l'exigence issue du texte (*« pénalisés »*) dont la formule d'application est absente. |
| **6. Équiper les 12 voitures de traceurs GPS pour suivi en temps réel.** | **Rejetée** | Fonctionnalité matérielle intrusive non sollicitée par le commanditaire. |

---

### Q11. Analyse d'une proposition plausible mais inventée par l'IA

* **Proposition analysée :**  
  > *« Le système doit envoyer une notification SMS au client 2 heures avant la fin du contrat et facturer automatiquement un supplément de 30 € par demi-heure de retard constatée. »*
* **Pourquoi elle est convaincante :**  
  Elle s'inspire du fonctionnement réel des grandes entreprises de location de voitures et semble apporter une solution prête à l'emploi au problème des retards.
* **Pourquoi elle est dangereuse :**  
  Elle impose des coûts techniques non prévus (passerelle SMS), invente un tarif arbitraire (30 € / 30 min) sans base légale ni accord du client, et complexifie l'architecture en imposant un système de facturation automatique en arrière-plan.

---

### Q12. Ambiguïté relevée par l'analyse critique

* **Ambiguïté :** Les modalités d'application et de contrôle de l'**offre spéciale week-end pour les familles**.
* **Explication :** Alors qu'on pense d'abord aux dates du week-end, l'analyse critique met en évidence une difficulté majeure : comment le système informatique en ligne contrôle-t-il la notion de « famille » ? S'agit-il d'un simple code promotionnel, d'une offre réservée à certaines catégories de véhicules spacieux (SUV/monospaces), ou d'un justificatif à fournir au comptoir lors de la remise des clés ?

