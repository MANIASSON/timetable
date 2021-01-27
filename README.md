# timetable

III. CREONS L'OBJET

SELECT DISTINCT T.jourCoursDate, C.codeCours
    FROM Cours C
    JOIN Typehoraire T
    ON C.codeCours= T.crsCodeCours
    JOIN Jourcours J
    ON J.dateJourCours=T.jourCoursDate
    JOIN Coursdeclasse cls
    ON  T.crsCodeCours=cls.crsCodeCours
    JOIN Classe Cl
    ON cl.specialiteNomSpec=cls.classSpecialiteNomspec
    ORDER BY T.jourCoursDate;
    
IV. ECRIVONS UN SCRIPT INTER-ACTIF

SELECT courCodeCours FROM Etudiantdeclasse WHERE etudiantMatricule =&matricule;

V. EMPLOI DE TEMPS

SET ECHO OFF
SET MARKUP HTML ON SPOOL ON
SPOOL emploi_temps_TIPAM2.HTML
SELECT DISTINCT C.codeCours, T.jourCoursDate,C.VOLUMEH FROM Cours C
JOIN Typehoraire T
ON C.codeCours= T.crsCodeCours
JOIN Jourcours J
ON J.dateJourCours=T.jourCoursDate
JOIN Coursdeclasse cls
ON T.crsCodeCours=cls.crsCodeCours
JOIN Classe Cl
ON cl.specialiteNomSpec=cls.classSpecialiteNomspec
JOIN Etudiantdeclasse et 
on cls.crsCodeCours=et.COURCODECOURS
JOIN ETUDIANT pp 
ON pp.MATRICULE=et.ETUDIANTMATRICULE
WHERE  et.ETUDIANTMATRICULE=&Matricule AND PASSWORD=&Password;
SPOOL OFF
SET MARKUP HTML OFF
SET ECHO ON
