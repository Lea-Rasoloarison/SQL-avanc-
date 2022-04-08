# SQL-avanc-
SQL avancé


1 - Retourne le nom des équipes et le nombre de joueurs par équipe, le tout classé par nombre de joueurs par équipe, de la plus nombreuse à la moins nombreuse.

SELECT name, COUNT(*) AS nb_student
FROM player
INNER JOIN school ON player.team_id=school.id
GROUP BY name;


2 - Retourne uniquement les noms des équipes complètes (ayant 14 joueurs ou plus, c’est-à- dire 7 joueurs et 7 remplaçants minimum), classés par ordre alphabétique.

SELECT name, COUNT(*) AS nb_student
FROM player
INNER JOIN school ON player.team_id=school.id
GROUP BY name
HAVING nb_student > 14;


3 - L’entraîneur des Gryffindor est superstitieux, son jour préféré est le lundi. Retourne la liste des joueurs de son équipe qui ont été enrôlés un lundi (il souhaite les faire jouer en priorité), et classe les résultats par date d’enrôlement chronologique.

SELECT CONCAT(firstname, ' ', lastname) AS fullname
FROM wizard
INNER JOIN player ON wizard.id=player.wizard_id
GROUP BY fullname
HAVING player.team_id = 1;
