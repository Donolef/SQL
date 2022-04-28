# SQL
2 projets 

Projets 1 : La musique dans la peau 🎸🎸

La musique dans la peau 🎸🎸
1. Introduction

Dans les deux projets du jour, tu vas pratiquer à fond le langage SQL, une compétence souvent indispensable pour devenir Data Aanalyst.
2. Le projet

Suite à THP, une startup trop cool spécialisée dans la musique te recrute pour tes compétences de Data Analyst. C'est la fête. Comme cette startup existe déjà depuis plusieurs années, ils ont une base de données existante, et vont te demander de travailler dessus.

Dans cet exercice, on te demande donc de récupérer une base de données existante, et de faire des requêtes SQL dedans, afin de récupérer les datas qui t'intéressent, et qui feront de toi une star de la musique.

Nous allons travailler sur le fichier suivant, qui contient la BDD complète pour faire les requêtes.
Tu devras rédiger les requêtes en langage SQL sur le SGBD de ton choix (tu peux travailler sur SQL online compiler si tu n'as pas de SGBD). Certaines requêtes avec des jointures ne seront pas faciles au premier abord, donc nous t'invitons à bien décortiquer les ressources que nous t'avons données 😉

Rédige les requêtes SQL permettant d'obtenir les informations ci-dessous. Consigne importante : la requête doit se faire en une seule ligne de SQL et ne doit pas s'appuyer sur d'autres requêtes (notamment pas les requêtes précédentes).

    Récupérer tous les albums
    Récupérer tous les albums dont le titre contient "Great" (indice)
    Donner le nombre total d'albums contenus dans la base (sans regarder les id bien sûr)
    Supprimer tous les albums dont le nom contient "music"
    Récupérer tous les albums écrits par AC/DC
    Récupérer tous les titres des albums de AC/DC
    Récupérer la liste des titres de l'album "Let There Be Rock"
    Afficher le prix de cet album ainsi que sa durée totale
    Afficher le coût de l'intégralité de la discographie de "Deep Purple"
    Créer l'album de ton artiste favori en base, en renseignant correctement les trois tables albums, artists et tracks

3. Rendu attendu

Un fichier .txt (ou .md) contenant les requêtes SQL qui permettent d'obtenir les infos demandées sur notre BDD musicale 🎶🎶


Projets 2 : 5 ans après, nouvelle enquête sur les Panama Papers

5 ans après, nouvelle enquête sur les Panama Papers
1. Introduction

Toujours comme ce matin pendant le cours OpenClassrooms (à relire si tu as un peu oublié), tu es dans la peau d'un journaliste d'investigation du Fronde qui doit ré-enquêter sur les Panama Papers. La revue pense qu'il faut re-sensibiliser le public aux découvertes faites en 2016.

A ce propos, le secrétaire de rédaction t'a retoqué hier ton article car selon lui, "il manque de données quantitatives et précises". Il te demande d'aller directement à la source de l'information, de reprendre toutes les données qui ont été rendues publiques à l'époque et de répondre à une longue liste de questions que se posent les lecteurs. Ces réponses pourront faire l'objet d'une infographie interactive, ce qui "plaira beaucoup plus aux lecteurs que ton histoire incompréhensible d'argent planqué".
2. Le projet

Télécharge la base de données ici et mets-toi dans la peau d'Hercule Poirot 🔎🔎

Voici la liste de questions auxquelles tu dois répondre :

    Combien la base de données contient-elle de sociétés offshores différentes dont la source est "Panama Papers" ?
    Quel intermédiaire a créé le plus de sociétés offshores ? A-t-on son adresse et son pays ?
    Combien la base contient-elle de bénéficiaires avec un nom unique ? Quel est le bénéficiaire dont le nom revient le plus souvent ?
    Donner la liste des juridictions avec le nombre d'entreprises offshores enregistrées sur chaque territoire, triée par ordre décroissant.
    Regrouper les sociétés offshores par statut, et trier la liste par ordre décroissant.
    Trouver la liste des bénéficiaires dont le nom contient "BNP" et ajouter, pour chaque bénéficiaire, le nom des sociétés offshores.
    Trouver la liste des sociétés dont la juridiction est "France", "Monaco" ou "Réunion".
    Trouver la liste des sociétés dont le pays de l'adresse et le pays de la juridiction sont différents.
    Trouver la liste des bénéficiaires qui ont des sociétés au même nom et enregistrée à la même date, trier la liste par odre décroissant.
    Donner la liste des intermédiaires qui ont aussi été bénéficiaires, en ajoutant leur nom de bénéficiaire et leur adresse.
    Donner le top 10 des bénéficiaires qui ont le plus d'identités différentes (similar name and address) et le nombre d'identités correspondant.
    Donner le top 10 des bénéficiaires qui ont le plus de parts toujours valides dans des entreprises offshores (dont la date de fin n'est pas encore passée).
    Question bonus : réussir à retrouver dans la base au moins 3 personnalités que tu connais (indice) 😎😎😎

3. Rendu attendu

Un fichier .txt (ou .md) contenant les requêtes SQL qui permettent d'obtenir les infos demandées sur notre BDD.
4. Aller plus loin

Alors tu as aimé te prendre pour Sherlock Holmes pendant 3 heures ? Ca t'a plu de travailler sur de vraies données ? A l'époque, c'était assez novateur comme type de journalisme : c'est une des affaires qui a aidé les grandes rédactions à se tourner davantage vers la Data.
Si cela t'intéresse, voici 2 ressources qui t'en diront plus sur comment ça s'est passé dans la vie réelle :

    un journaliste du Monde qui raconte les 9 mois passés à travailler sur cette base de données
    un long mémoire dont la thématique était "Les “Panama Papers” marquent-ils l’émergence de pratiques professionnelles et journalistiques nouvelles ?". Tu peux faire des recherchers (Ctrl F) et checker les moments où l'auteur parle de data ou données. Tu verras que la data analyse n'a malheureusement pas été la compétence la plus répandue dans cette affaire ... En fait, si on avait créé la formation Data 5 ans plus tôt, t'aurais vraiment pu être ce journaliste star 😅😅


