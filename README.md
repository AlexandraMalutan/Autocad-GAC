# Autocad-GAC


PROIECT 2- MODIFICAREA UNUI DESEN FOLOSIND AUTOLISP


	(defun c:dimensiunecerc (/ ss contor entitate dimensiuneinitiala dimensiunenoua); definim functia si ii dam nume
	  (setq ss (ssget "_X" '((0 . "CIRCLE")))); facem o selectie a tuturor entitatilor care sunt cercuri
	  (setq contor 0); initializam contorul cu 0
	      (repeat (sslength ss); repetam codul atata timp cat mai exista cercuri
	        (setq entitate (ssname ss contor)); selectez obiectul curent
	        (setq dimensiuneinitiala (cdr (assoc 40 (entget entitate)))); preiau raza cercului curent reprezentat de variabila entitate si o stochez in dimensiuneinitiala
	        (setq dimensiunenoua (getdist (strcat "\nIntrodu noua dimensiune a cercului #" (itoa (1+ contor)) ": ")));expresia ne solicita sa introducem o noua raza pt cercul curent, a carei valoare se stocheaza in variabila dimensiunenoua
	        (entmod (subst (cons 40 dimensiunenoua) (assoc 40 (entget entitate)) (entget entitate))); modificam raza initiala cu valoarea stocata in dimensiunenoua
	        (setq contor (1+ contor));trecem la urmatorul cerc
	      )
	  (princ)
	)
