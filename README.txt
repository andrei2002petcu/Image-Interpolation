###############################################################################
############################# README - Tema_2 MN ##############################
###############################################################################

Toate functiile au fost implementate urmand strict TODO-urile si indicatiile
din PDF. Apelurile functiei 'f' din cadrul programelor necesita interschimbarea
celor 2 parametrii -> f(y, x), in loc de f(x, y)

############################ Interpolare proximala ############################

-> proximal_2x2.m
	Pentru aflarea celui mai apropiat pixel, se vor calcula distantele dintre
	pixelii initiali (din imaginea sursa) si pixelul nou rezultat. Se va alege
	distanta minima, iar pixelul nou va primi valoarea din punctul respectiv.
	In plus functia abordeaza separat cazurile in care punctul se afla pe
	oricare dintre forntiere.
-> proximal_resize.m
	Functia urmareste fiecare pas descris de TODO si PDF: calculeaza factorii
	de scalare, matricea de transformare si inversa ei. Se vor parcurge toti
	pixelii, aplicand matricea asupra x si y, apoi se trec valorile rezultate 
	in sistemul de coordonate [1, n] si se calculeaza pixelul cel mai apropiat
	(folosind 'round' pt. rotunjire). Valoarea pixelului final este rezultat 
	pe baza valorii sale initiale si a celui mai apropiat pixel, calculat 
	anterior.
->  proximal_rotate.m
	Functia urmareste fiecare pas descris de TODO si PDF: calculeaza matricea 
	de transformare si inversa ei (in functie de unghiul de rotatie dat) si
	parcurge fiecare pixel. Se va aplica matricea de transformare si se vor
	trece punctele in sistemul de coordonate [1, n] (prin deplasare cu 1).
	Functia va calula punctele inconjuratoare si coeficientii de interpolare,
	apeland functia 'proximal_coef.m' (implementata similar cu bicubic_coef.m
	descrisa ma jos). In final, pixelul rotit va fi calculat folosind formula
	descrisa in PDF.

############################# Interpolare bicubica ############################

-> fx.m && fy.m && fxy.m
	Functiile aproximeaza derivatele pe baza formulelor prezentate in PDF. Se
	trateaza si cazul de baza, derivatele devenind 0 la marginile imaginii.
-> precalc_d.m
	Pentru completarea matricilor Ix, Iy, Ixy, se va parcurge fiecare pixel
	calculand derivata corespunzatoare, cu ajutorul functiilor fx, fy, fxy.
-> bicubic_coef.m
	Pentru calculul coeficientilor, au fost urmati strict pasii prezentati
	in PDF. S-au definit cei 2 vectori cu valorile necesare, matricea
	urmarind formulele, iar in final coeficientii sunt aflati prin inmultirea
	tuturor elementelor citate.
-> bicubic_resize.m
	Functia este similara cu 'proximal_resize': calculeaza factorii de scalare,
	matricea de transformare si inversa ei. In plus, calculeaza, cu ajutorul
	functiei 'precalc_d.m', cele 3 matrici ce contin aproximatiile derivatelor.
	Se parcurge fiecare pixel aplicand matricea de transformare si deplasand
	valorile cu '1'. 
	Se vor gasi cele 4 puncte ce inconjoara pixelul initial si se calculeaza
	coeficientii. Coordonatele se deplaseaza in patratul unitate, iar pixelul
	final va fi calculat conform formulei descrise in PDF.

################################# Functiile 'RGB' #############################
	
Pentru toate functiile RGB implementate, am extras cele 3 canale de culori ale
imaginii si am aplicat interpolarea/ rotate-ul/ resize-ul pe fiecare, apeland
functiile descrise mai sus. Imaginea finala se realizeaza folosind 'cat' pentru
cele 3 matrici.

###############################################################################
Facultatea de Automatica si Calculatoare - Anul 1 2021-2022 - Grupa 312CCa
PETCU Andrei - Metode Numerice - TEMA 2
###############################################################################