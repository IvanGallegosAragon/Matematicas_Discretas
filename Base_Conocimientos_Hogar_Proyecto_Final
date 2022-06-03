% lugares
	lugar(sala).
	lugar(cuarto).
	lugar(bano).
	lugar(cocina).
	lugar(entrada).
	lugar(patio).

% Objetos
	% mesa de estrcutra (Color,Forma,Material,Ubicacion)  
		mesa(cafe,rectangular,madera,patio).
		mesa(blanco,rectangular,metal,sala).
		mesa(amarillo,rectangular,metal,cocina).
		mesa(transparente,ovalado,cristal,sala).

	% sofa de estrcutra (Color,Forma,Unicacion)  
		sofa(blanco,rectangular,sala).
		sofa(cafe,rectangular,patio).
		sofa(blanco,cuadrado,sala).

	% television de estrcutra (Tipo, Ubicacion)
		television(plana,sala).
		television(plana,cuarto).

	% sillas de estrcutra (Color, Material, Ubicacion)
		silla(blanco, plastico, cuarto).
		silla(cafe,madera,patio).
		silla(cafe,madera,patio).
		silla(cafe,madera,patio).
		silla(cafe,madera,patio).
		silla(blanco,plastico,sala).
		silla(blanco,plastico,sala).
		silla(blanco,plastico,sala).
		silla(blanco,plastico,sala).
		silla(blanco,plastico,sala).
		silla(blanco,plastico,sala).
		silla(cafe,plastico,cocina).
		silla(cafe,plastico,cocina).

	% lamparas de estrcutra (Tipo,Forma,Ubicacion)
		lampara(techo,doble,sala).
		lampara(techo,barra,cocina).
		lampara(techo,plana,entrada).
		lampara(techo,telarana,sala).
		lampara(techo,cuadruple,bano).
		lampara(techo,doble,cuarto).
		lampara(mesa,copa,cuarto).
		lampara(mesa,copa,cuarto).
		lampara(techo,red,patio).

	% cama de estrcutra (Tipo,Ubicacion)
		cama(matrimonial,cuarto).

	% espejos de estrcutra (Tamaño, Ubicacion)
		espejo(mediano,bano).
		espejo(mediano,bano).
		espejo(grande,cuarto).
		espejo(mediano,entrada).
		espejo(mediano,sala).

	% pintura de estrcutra (Tamano, Imagen, Ubicacion).
		pintura(grande,rostro,sala).
		pintura(mediano,paisaje,cuarto).
		pintura(pequeno,ojo,entrada).
		pintura(pequeno,popArt,cocina).
		pintura(pequeno,popArt,cocina).

	% maceta de estrcutra (Tamano, Ubicacion).
		maceta(pequeno, bano).
		maceta(mediano, bano).
		maceta(mediano, sala).
		maceta(mediano, patio).
		maceta(mediano, patio).
		maceta(mediano, patio).
		maceta(pequeno, patio).
		maceta(pequeno, patio).

	% florero de estrcutra  (Tamano, Ubicacion)
		florero(pequeno,entrada).
		florero(mediano,sala).

	% horno de estrcutra (Color,Tipo,Unicacion)
		horno(cafe,ladrillo,patio).
		horno(blanco,microndas,cocina).
		horno(blanco,estufa,cocina).

	% retrete de estrcutra (Color, Ubicacion)
		retrete(blanco,bano).

	% regadera de estrcutra (Color,Ubicacion).
		regadera(transparente,bano).

	% tapete de estrcutra (Color, Tamano, Ubicacion)
		tapete(gris,pequeno,cuarto).
		tapete(gris,pequeno,cuarto).
		tapete(gris,grande,entrada).
		tapete(pelusa,pequeno,bano).
		tapete(pelusa,pequeno,bano).
		tapete(azul,grande,sala).

	% ventana de estrcutra (Tamano, Ubicacion).
		ventana(grande,sala).
		ventana(mediano,cuarto).

	% relog de estrcutra (Color, Tamano, Ubicacion)
		relog(negro,mediano,cocina).

	% gabinete de estrcutra (Color,Tamano,Unicacion)
		gabinete(cafe,pequeno,bano).
		gabinete(negro,mediano,cuarto).
		gabinete(gris,mediano,sala).
		gabinete(cafe,mediano,cocina).
		gabinete(amarillo,grande,cocina).
		gabinete(amarillo,mediano,cocina).

	% refrigerador de estrcutra (Color,Ubicacion).
		refrigerador(amarillo,cocina).

	% lavabo de estrcutra (Color,Tipo,Ubicacion).
		lavabo(blanco,manos,bano).
		lavabo(gris,trastes,cocina).


% Relaciónes de adyacencia entre lugares tipo conecta(Lugar1,Lugar2,Direccion,Referencia)
	conecta(entrada,bano,derecha,'con la puerta de entrada a tus espaldas').
	conecta(bano,entrada,derecha,'mirando el labamanos').

	conecta(entrada,cuarto,de_frente,'con la puerta de entrada a tus espaldas').
	conecta(cuarto,entrada,izquierda,'con la cama a tus espaldas').

	conecta(entrada,sala,izquierda,'con la puerta de entrada a tus espaldas').
	conecta(sala,entrada,de_frente,'con la television a tus espaldas').

	conecta(cuarto,patio,derecha, 'con la cama a tus espaldas').
	conecta(patio,cuarto,de_fente,'con el horno a tus espaldas').

	conecta(sala,cocina,derecha,'con la television a tus espaldas').
	conecta(cocina,sala,de_frente,'con la estufa a tus espaldas').

% Lugares que con los que se conecta un lugar, recibe un lugar de la casa.
% Ej: lugares_que_conecta(sala)

	lugares_que_conecta(Lugar):- findall(Lugares,conecta(Lugar,Lugares,_,_),Lista), length(Lista,Longitud),
	(Longitud is 1 ->  write('Es'),writeln(Longitud),writeln('Solo se conecta con: '),mostrarlista(Lista);
		write('Son '),writeln(Longitud),writeln('Son los siguientes: '), mostrarlista(Lista)).

% Indicaciónes de como ir a lugares de la casa desde la entrada, el camino mas largo solo tiene 3 eslabones.
% recibe un lugar de la casa. Ej: indicacion_entrada(sala)

	indicacion_entrada(Destino):- 
	(conecta(entrada,Destino,Direccion,Referencia) -> % if
		write('Desde la entrada, '),write(Referencia), write(' avanza hacia la direccion '), 
		write(Direccion),writeln( ' y entra.'); 
	
	(conecta(entrada,Lugar1,Direccion1,Referencia1), conecta(Lugar1,Destino,Direccion2,Referencia2) ->  % if else
		write('Desde la entrada, '),write(Referencia1), write(' avanza hacia la direccion '), write(Direccion1),writeln(', entra, despues '), 
		write(Referencia2), write(' avanza hacia la direccion '), write(Direccion2), writeln(' y entra.'); 
	
	(conecta(entrada,Lugar2,Direccion3,Referencia3),conecta(Lugar2,Lugar3,Direccion4,Referencia4), conecta(Lugar3,Destino,Direccion5,Referencia5) -> % if else
		write('Desde la entrada, '),write(Referencia3), write(' avanza hacia la direccion '), write(Direccion3),writeln(', entra, despues '),
		write(Referencia4), write(' avanza hacia la direccion '), write(Direccion4), writeln(', entra, y por utlimo '), write(Referencia5), 
		write(' avanza hacia la direccion '), write(Direccion5),writeln(' y entra.');
	
	writeln('No existe dicho lugar en la casa')))). % else


% Indicaciones de como ir a lugares desde un lugar A a un lugar B, igual, el maximo eslabon es de 3
% recibe el lugar de Inicio y el Destino. Ej: indicacion(sala,bano)
	indicacion(Inicio,Destino):- 
	(conecta(Inicio,Destino,Direccion,Referencia) -> 
		write('Desde la habitacion '),write(Inicio), write(', '),write(Referencia), 
		write(' avanza hacia la direccion '), write(Direccion),writeln( ' y entra.'); 

	(conecta(Inicio,Lugar1,Direccion1,Referencia1), conecta(Lugar1,Destino,Direccion2,Referencia2) ->  
		write('Desde la habitacion '),write(Inicio), write(', '),write(Referencia1), write(' avanza hacia la direccion '), write(Direccion1),
		writeln(', entra, despues '), write(Referencia2), write(' avanza hacia la direccion '), write(Direccion2), writeln(' y entra.'); 

	(conecta(Inicio,Lugar2,Direccion3,Referencia3),conecta(Lugar2,Lugar3,Direccion4,Referencia4), conecta(Lugar3,Destino,Direccion5,Referencia5) ->
		write('Desde la habitacion '),write(Inicio), write(', '),write(Referencia3), write(' avanza hacia la direccion '), write(Direccion3),
		writeln(', entra, despues '),write(Referencia4), write(' avanza hacia la direccion '), write(Direccion4), 
		writeln(' y entra, por utlimo '), write(Referencia5), write(' avanza hacia la direccion '), write(Direccion5),writeln(' y entra.');

	writeln('No existe dicho lugar en la casa')))). 

% Existe un objeto, cuya entrada es un objeto en estrcutra de predicado.
% Ej: existe_objeto( lampara(mesa,copa,cuarto) )

	existe_objeto(Objeto):- (Objeto -> writeln('Si existe');writeln('No existe')).

% Lista renglon por renglon de todos los objetos listados, descritos conforme a su estrcutra.
% No necesita varaible de entrada 

	listar_mesas:-
	writeln('Todas las mesas con estructura (Color,Forma,Material,Ubicacion): '), 
	findall(('Una mesa de color',Color,'de forma',Forma,'de material',Material,'en',Ubicacion),
		mesa(Color,Forma,Material,Ubicacion),Mesas), write('Son:'), length(Mesas,Longitud), writeln(Longitud), 
	(Longitud is 1 -> writeln('El cual es: '),mostrarlista(Mesas);
	 	writeln('Las cuales son: '), mostrarlista(Mesas)).

	listar_sofas:- writeln('Todos los sofas con estructura (Color,Forma,Ubicacion) '), 
	findall(('Un sofa de color',Color,'con forma',Forma,'en',Ubicacion),
		sofa(Color,Forma,Ubicacion),Sofas),write('Son:'), length(Sofas,Longitud), writeln(Longitud),
	(Longitud is 1 -> writeln('El cual es: '),mostrarlista(Sofas);
	 	writeln('Las cuales son: '), mostrarlista(Sofas)).

	listar_televisiones:- writeln('Todas las televisiones con estructura (Tipo,Ubicacion) '),
	findall(('Una television tipo',Tipo,'en',Ubicacion),
		television(Tipo,Ubicacion),Teles), write('Son:'), length(Teles,Longitud), writeln(Longitud),
	(Longitud is 1 -> writeln('El cual es: '),mostrarlista(Teles);
	 	writeln('Las cuales son: '), mostrarlista(Teles)).

	listar_sillas:-  writeln('Todas las sillas con estructura (Color, Material, Ubicacion): '), 
	findall(('Hay una silla de color',Color,'de material',Material,'en',Ubicacion),
		silla(Color, Material, Ubicacion),Sillas),write('Son:'), length(Sillas,Longitud), writeln(Longitud),
	(Longitud is 1 -> writeln('El cual es: '),mostrarlista(Sillas);
	 	writeln('Las cuales son: '), mostrarlista(Sillas)).

	listar_lamparas:-  writeln('Todas las lamaparas con estructura (Tipo,Forma,Ubicacion): '), 
	findall(('Hay una lampara de tipo',Tipo,'de forma',Forma,'en',Ubicacion),
		lampara(Tipo,Forma,Ubicacion),Lamparas), write('Son:'), length(Lamparas,Longitud), writeln(Longitud),
	(Longitud is 1 -> writeln('El cual es: '),mostrarlista(Lamparas);
	 	writeln('Las cuales son: '), mostrarlista(Lamparas)).

	listar_camas:- writeln('Todas las camas con estructura (Tipo,Ubicacion): '), 
	findall(('Hay una cama de tipo',Tipo,'en',Ubicacion),
		cama(Tipo,Ubicacion),Camas),write('Son:'), length(Camas,Longitud), writeln(Longitud),
	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Camas);
	 	writeln('Las cuales son: '), mostrarlista(Camas)).

	listar_espejos:- writeln('Todos los espejos con estructura (Tamano, Ubicacion): '), 
	findall(('Hay un espejo de tamano',Tamano,'en' ,Ubicacion),
		espejo(Tamano, Ubicacion),Espejos),write('Son:'), length(Espejos,Longitud), writeln(Longitud),
	(Longitud is 1 -> writeln('El cual es: '),mostrarlista(Espejos);
	 	writeln('Las cuales son: '), mostrarlista(Espejos)).

	listar_pinturas:- writeln('Todas las pinturas con estructura (Tamano, Imagen, Ubicacion): '), 
	findall(('Hay una pintura de tamano',Tamano,'con la imagen de',Imagen,'en',Ubicacion),
		pintura(Tamano, Imagen, Ubicacion),Pinturas),write('Son:'), length(Pinturas,Longitud), writeln(Longitud),
	(Longitud is 1 -> writeln('El cual es: '),mostrarlista(Pinturas);
	 	writeln('Las cuales son: '), mostrarlista(Pinturas)).

	listar_macetas:- writeln('Todas las macetas con estructura (Tamano, Ubicacion): '), 
	findall(('Hay una maceta de tamano',Tamano,'en',Ubicacion),
		maceta(Tamano, Ubicacion),Macetas), write('Son:'), length(Macetas,Longitud), writeln(Longitud),
	(Longitud is 1 -> writeln('El cual es: '),mostrarlista(Macetas);
	 	writeln('Las cuales son: '), mostrarlista(Macetas)).

	 listar_floreros:- writeln('Todos los floreros con estructura (Tamano, Ubicacion): '), 
	findall(('Hay un florero de tamano',Tamano,'en',Ubicacion),
		florero(Tamano, Ubicacion),Floreros), write('Son:'), length(Floreros,Longitud), write(Longitud),nl,
	(Longitud is 1 -> writeln('El cual es: '),mostrarlista(Floreros);
	 	writeln('Las cuales son: '), mostrarlista(Floreros)).

	 listar_hornos:- writeln('Todos los hornos con estructura (Color,Tipo,Ubicacion): '), 
	findall(('Hay un horno de color',Color,'de tipo',Tipo,'en',Ubicacion),
		horno(Color,Tipo,Ubicacion),Hornos),write('Son:'), length(Hornos,Longitud), write(Longitud),nl,
	(Longitud is 1 -> writeln('El cual es: '),mostrarlista(Hornos);
	 	writeln('Las cuales son: '), mostrarlista(Hornos)).

	listar_retretes:- writeln('Todos los retretes con estructura (Color, Ubicacion): '), 
	findall(('Hay un retrete de color',Color,'en',Ubicacion),
		retrete(Color, Ubicacion),Retretes), write('Son:'), length(Retretes,Longitud), writeln(Longitud),
	(Longitud is 1 -> writeln('El cual es: '),mostrarlista(Retretes);
	 	writeln('Las cuales son: '), mostrarlista(Retretes)).

	listar_regaderas:- writeln('Todas las regaderas con estructura (Color,Ubicacion): '), 
	findall(('Hay una regadera de color',Color,'en',Ubicacion),
		regadera(Color,Ubicacion),Regaderas),write('Son:'), length(Regaderas,Longitud), writeln(Longitud),
	(Longitud is 1 -> writeln('El cual es: '),mostrarlista(Regaderas);
	 	writeln('Las cuales son: '), mostrarlista(Regaderas)).

	listar_tapetes:- writeln('Todos los tapetes con estructura (Color, Tamano, Ubicacion): '), 
	findall(('Hay un tapete de color',Color,'de tamano',Tamano,'en',Ubicacion),
		tapete(Color, Tamano, Ubicacion),Tapetes), write('Son:'), length(Tapetes,Longitud), writeln(Longitud),
	(Longitud is 1 -> writeln('El cual es: '),mostrarlista(Tapetes);
	 	writeln('Las cuales son: '), mostrarlista(Tapetes)).

	 listar_ventanas:- writeln('Todas las ventanas con estructura (Tamano, Ubicacion): '), 
	findall(('Hay una ventana de tamano',Tamano,'en',Ubicacion),
		ventana(Tamano, Ubicacion),Ventanas),write('Son:'), length(Ventanas,Longitud), writeln(Longitud),
	(Longitud is 1 -> writeln('El cual es: '),mostrarlista(Ventanas);
	 	writeln('Las cuales son: '), mostrarlista(Ventanas)).
	
	listar_relogs:- writeln('Todos los relogs con estructura (Color, Tamano, Ubicacion): '), 
	findall(('Hay un relog de color',Color,'de tamano',Tamano,'en',Ubicacion),
		relog(Color, Tamano, Ubicacion),Relogs), write('Son:'), length(Relogs,Longitud), writeln(Longitud),
	(Longitud is 1 -> writeln('El cual es: '),mostrarlista(Relogs);
	 	writeln('Las cuales son: '), mostrarlista(Relogs)).
	
	listar_gabinetes:- writeln('Todos los gabinetes con estructura (Color,Tamano,Ubicacion): '), 
	findall(('Hay un gabinete de color',Color,'de tamano',Tamano,'en',Ubicacion),
		gabinete(Color,Tamano,Ubicacion),Gabinetes), write('Son:'), length(Gabinetes,Longitud), writeln(Longitud),
	(Longitud is 1 -> writeln('El cual es: '),mostrarlista(Gabinetes);
	 	writeln('Las cuales son: '), mostrarlista(Gabinetes)).

	listar_refrigeradores:- writeln('Todos los refrigeradores con estructura (Color, Ubicacion): '), 
	findall(('Hay un refrigerador de color',Color,'en',Ubicacion),
		refrigerador(Color, Ubicacion),Refrigeradores), write('Son:'), length(Refrigeradores,Longitud), writeln(Longitud),
	(Longitud is 1 -> writeln('El cual es: '),mostrarlista(Refrigeradores);
	 	writeln('Las cuales son: '), mostrarlista(Refrigeradores)).

	listar_lavabos:- writeln('Todos los lavabos con estructura (Color,Tipo,Ubicacion): '), 
	findall(('Hay un lavabo de color',Color,'de tipo',Tipo,'en',Ubicacion),
		lavabo(Color,Tipo,Ubicacion),Lavabos),write('Son:'), length(Lavabos,Longitud), writeln(Longitud),
	(Longitud is 1 -> writeln('El cual es: '),mostrarlista(Lavabos);
	 	writeln('Las cuales son: '), mostrarlista(Lavabos)).


% Lista y describe los elementos solicitados, esta solicitud alude a algun atributo del objeto.
% recibe un ejemplo del atributo pedido. Ej: lista_macetas_en(sala), este infiere un lugar el prefijo _en
	
	lista_mesas_en(Lugar):-
		findall(('Hay una mesa de color',Color,'con forma',Forma,'de material',Material,'en',Lugar),
		mesa(Color,Forma,Material,Lugar),Mesas),write('Son:'), length(Mesas,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Mesas);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Mesas);
	 	writeln('No hay'))).

	lista_mesas_de_color(Color):-  
		findall(('Hay una mesa de forma',Forma,'de material',Material,'en',Lugar,'de color',Color),
		mesa(Color,Forma,Material,Lugar),Mesas),write('Son:'), length(Mesas,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Mesas);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Mesas);writeln('No hay'))).

	lista_mesas_con_forma(Forma):-  
		findall(('Hay una mesa de color',Color,'de material',Material,'en',Lugar,'con forma',Forma),
		mesa(Color,Forma,Material,Lugar),Mesas),write('Son:'), length(Mesas,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Mesas);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Mesas);writeln('No hay'))).


	lista_mesas_de_material(Material):-
	 	findall(('Hay una mesa de color',Color,'de forma',Forma,'en',Lugar,'de',Material),
	 	mesa(Color,Forma,Material,Lugar),Mesas), write('Son:'), length(Mesas,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Mesas);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Mesas);writeln('No hay'))).

	 lista_sofas_en(Lugar):-
	 findall(('Hay un sofa de color',Color,'de forma',Forma,'en',Lugar),
	 	sofa(Color,Forma,Lugar),Sofas),write('Son:'), length(Sofas,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Sofas);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Sofas);writeln('No hay'))).

	 lista_sofas_con_froma(Forma):-
	 findall(('Hay un sofa de color',Color,'en',Lugar,'con forma',Forma),
	 	sofa(Color,Forma,Lugar),Sofas),write('Son:'), length(Sofas,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Sofas);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Sofas);writeln('No hay'))).

	 lista_sofas_de_color(Color):-
	 findall(('Hay un sofa de forma',Forma,'en',Lugar,'de color',Color),
	 	sofa(Color,Forma,Lugar),Sofas),write('Son:'), length(Sofas,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Sofas);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Sofas);writeln('No hay'))).


	 lista_televisiones_de_tipo(Tipo):-
	 findall(('Hay una television en',Lugar,'de tipo',Tipo),
	 	television(Tipo,Lugar),Televisiones),write('Son:'), length(Televisiones,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Televisiones);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Televisiones);writeln('No hay'))).

	 lista_televisiones_en(Lugar):-
	 findall(('Hay una television de tipo',Tipo,'en',Lugar),television(Tipo,Lugar),Televisiones),
		write('Son:'), length(Televisiones,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Televisiones);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Televisiones);writeln('No hay'))).

	  lista_sillas_en(Lugar):-
	 findall(('Hay una silla de color',Color,'de material',Material,'en',Lugar),
	 	silla(Color,Material,Lugar),Sillas),write('Son:'), length(Sillas,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Sillas);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Sillas);writeln('No hay'))).

	 lista_sillas_de_material(Material):-
	 findall(('Hay una silla de color',Color,'en',Lugar,'de material',Material),
	 	silla(Color,Material,Lugar),Sillas),write('Son:'), length(Sillas,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Sillas);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Sillas);writeln('No hay'))).

	 lista_sillas_de_color(Color):-
	 findall(('Hay una silla de material',Material,'en',Lugar,'de color',Color),
	 	silla(Color,Material,Lugar),Sillas),write('Son:'), length(Sillas,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Sillas);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Sillas);writeln('No hay'))).


	  lista_lamparas_en(Lugar):-
	 findall(('Hay una lampara de tipo',Tipo,'con forma',Forma,'en',Lugar),
	 	lampara(Tipo,Forma,Lugar),Lamparas),write('Son:'), length(Lamparas,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Lamparas);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Lamparas);writeln('No hay'))).

	 lista_lamparas_con_froma(Forma):-
	 findall(('Hay una lampara de tipo',Tipo,'en',Lugar,'con forma',Forma),
	 	lampara(Tipo,Forma,Lugar),Lamparas),write('Son:'), length(Lamparas,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Lamparas);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Lamparas);writeln('No hay'))).

	 lista_lamparas_de_tipo(Tipo):-
	 findall(('Hay una lampara con forma',Forma,'en',Lugar,'de tipo',Tipo),
	 	lampara(Tipo,Forma,Lugar),Lamparas),write('Son:'), length(Lamparas,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Lamparas);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Lamparas);writeln('No hay'))).


	 lista_camas_de_tipo(Tipo):-
	 findall(('Hay una cama en',Lugar,'de tipo',Tipo),
	 	cama(Tipo,Lugar),Camas),write('Son:'), length(Camas,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Camas);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Camas);writeln('No hay'))).

	 lista_camas_en(Lugar):-
	 findall(('Hay una cama de tipo',Tipo,'en',Lugar),
	 	cama(Tipo,Lugar),Camas),write('Son:'), length(Camas,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Camas);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Camas);writeln('No hay'))).

	 lista_espejos_de_tamano(Tamano):-
	 findall(('Hay un espejo en',Lugar,'de tamano',Tamano),
	 	espejo(Tamano,Lugar),Espejos),
		write('Son:'), length(Espejos,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Espejos);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Espejos);writeln('No hay'))).

	 lista_espejos_en(Lugar):-
	 findall(('Hay un espejo de tamano',Tamano,'en',Lugar),
	 	espejo(Tamano,Lugar),Espejos),write('Son:'), length(Espejos,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Espejos);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Espejos);writeln('No hay'))).

	 	
	 lista_pinturas_en(Lugar):-
	 findall(('Hay una pintura de tamano',Tamano,'con la siguiente imagen,',Imagen,'en',Lugar),
	 	pintura(Tamano,Imagen,Lugar),Pinturas),
		write('Son:'), length(Pinturas,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Pinturas);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Pinturas);writeln('No hay'))).

	 lista_pinturas_con_imagen_de(Imagen):-
	 findall(('Hay una pintura de tamano',Tamano,'en',Lugar,'con una imagen de',Imagen),
	 	pintura(Tamano,Imagen,Lugar),Pinturas),write('Son:'), length(Pinturas,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Pinturas);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Pinturas);writeln('No hay'))).

	 lista_pinturas_de_tamano(Tamano):-
	 findall(('Hay una pintura con la imagen siguiente,',Imagen,'en',Lugar,'de tamano',Tamano),
	 	pintura(Tamano,Imagen,Lugar),Pinturas), write('Son:'), length(Pinturas,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Pinturas);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Pinturas);writeln('No hay'))).

		 	
	lista_macetas_de_tamano(Tamano):-
	findall(('Hay una maceta en',Lugar,'de tamano',Tamano),
		maceta(Tamano,Lugar),Macetas),write('Son:'), length(Macetas,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Macetas);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Macetas);writeln('No hay'))).

	lista_macetas_en(Lugar):-
	findall(('Hay una maceta de tamano',Tamano,'en',Lugar),
	 	maceta(Tamano,Lugar),Macetas),
		write('Son:'), length(Macetas,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Macetas);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Macetas);writeln('No hay'))).

	 	
	lista_floreros_de_tamano(Tamano):-
	findall(('Hay un florero en',Lugar,'de tamano',Tamano),
	 	florero(Tamano,Lugar),Floreros),write('Son:'), length(Floreros,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Floreros);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Floreros);writeln('No hay'))).

	lista_floreros_en(Lugar):-
	findall(('Hay un florero de tamano',Tamano,'en',Lugar),
	 	florero(Tamano,Lugar),Floreros),write('Son:'), length(Floreros,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Floreros);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Floreros);writeln('No hay'))).

	 	
	lista_hornos_en(Lugar):-
	findall(('Hay un horno de color',Color,'de tipo',Tipo,'en',Lugar),
		horno(Color,Tipo,Lugar),Hornos),
		write('Son:'), length(Hornos,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Hornos);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Hornos);writeln('No hay'))).

	 lista_hornos_de_tipo(Tipo):-
	 findall(('Hay un horno de color',Color,'en',Lugar,'de tipo',Tipo),horno(Color,Tipo,Lugar),Hornos),
		write('Son:'), length(Hornos,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Hornos);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Hornos);writeln('No hay'))).	

	 lista_hornos_de_color(Color):-
	 findall(('Hay un horno de tipo',Tipo,'en',Lugar,'de color',Color),
	 	horno(Color,Tipo,Lugar),Hornos),write('Son:'), length(Hornos,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Hornos);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Hornos);writeln('No hay'))).

	 	
	 lista_retretes_de_color(Color):-
	 findall(('Hay un retrete en',Lugar,'de color',Color),
	 	retrete(Color,Lugar),Retretes),write('Son:'), length(Retretes,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Retretes);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Retretes);writeln('No hay'))).

	 lista_retretes_en(Lugar):-
	 findall(('Hay un retretede color',Color,'en',Color),
	 	retrete(Color,Lugar),Retretes),write('Son:'), length(Retretes,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Retretes);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Retretes);writeln('No hay'))).


	 lista_regaderas_de_color(Color):-
	 findall(('Hay una regadera en',Lugar,'de color',Color),
	 	regadera(Color,Lugar),Regaderas),write('Son:'), length(Regaderas,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Regaderas);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Regaderas);writeln('No hay'))).

	 lista_regaderas_en(Lugar):-
	 findall(('Hay una regadera de color',Color,'en',Lugar),
	 	regadera(Color,Lugar),Regaderas),
		write('Son:'), length(Regaderas,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Regaderas);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Regaderas);writeln('No hay'))).


	lista_tapetes_en(Lugar):-
	findall(('Hay un tapete de color',Color,'de tamano',Tamano,'en',Lugar),
		tapete(Color,Tamano,Lugar),Tapetes),write('Son:'), length(Tapetes,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Tapetes);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Tapetes);writeln('No hay'))).

	 lista_tapetes_de_tamano(Tamano):-
	 findall(('Hay un tapete de color',Color,'en',Lugar,'de tamano',Tamano),
	 	tapete(Color,Tamano,Lugar),Tapetes),
		write('Son:'), length(Tapetes,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Tapetes);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Tapetes);writeln('No hay'))).	

	 lista_tapetes_de_color(Color):-
	 findall(('Hay un tapete de tamano',Tamano,'en',Lugar,'de color',Color),
	 	tapete(Color,Tamano,Lugar),Tapetes),write('Son:'), length(Tapetes,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Tapetes);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Tapetes);writeln('No hay'))).
	
	
	 lista_ventanas_de_tamano(Tamano):-
	 findall(('Hay una ventana en',Lugar,'de tamano',Tamano),
	 	ventana(Tamano,Lugar),Ventanas),write('Son:'), length(Ventanas,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Ventanas);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Ventanas);writeln('No hay'))).

	 lista_ventanas_en(Lugar):-
	 findall(('Hay una ventana de tamano',Tamano,'en',Lugar),
	 	ventana(Tamano,Lugar),Ventanas),
		write('Son:'), length(Ventanas,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Ventanas);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Ventanas);writeln('No hay'))).
	
	
	 lista_relogs_en(Lugar):-
	 findall(('Hay un relog de color',Color,'de tamano',Tamano,'en',Lugar),
	 	relog(Color,Tamano,Lugar),Relogs),write('Son:'), length(Relogs,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Relogs);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Relogs);writeln('No hay'))).

	 lista_relogs_de_tamano(Tamano):-
	 findall(('Hay un relog de color',Color,'en',Lugar,'de tamano',Tamano),
	 	relog(Color,Tamano,Lugar),Relogs),write('Son:'), length(Relogs,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Relogs);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Relogs);writeln('No hay'))).	

	 lista_relogs_de_color(Color):-
	 findall(('Hay un relog de tamano',Tamano,'en',Lugar,'de color',Color),
	 	relog(Color,Tamano,Lugar),Relogs),write('Son:'), length(Relogs,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Relogs);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Relogs);writeln('No hay'))).

	
	lista_gabinetes_en(Lugar):-
	 findall(('Hay un gabinete de color',Color,'de tamano',Tamano,'en',Lugar),
	 	gabinete(Color,Tamano,Lugar),Gabinetes),write('Son:'), length(Gabinetes,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Gabinetes);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Gabinetes);writeln('No hay'))).

	 lista_gabinetes_de_tamano(Tamano):-
	 findall(('Hay un gabinete de color',Color,'en',Lugar,'de tamano',Tamano),
	 	gabinete(Color,Tamano,Lugar),Gabinetes),write('Son:'), length(Gabinetes,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Gabinetes);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Gabinetes);writeln('No hay'))).

	 lista_gabinetes_de_color(Color):-
	 findall(('Hay un gabinete de tamano',Tamano,'en',Lugar,'de color',Color),
	 	gabinete(Color,Tamano,Lugar),Gabinetes),write('Son:'), length(Gabinetes,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Gabinetes);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Gabinetes);writeln('No hay'))). 	

	 lista_refrigeradores_de_color(Color):-
	 findall(('Hay un refrigerador en',Lugar,'de color',Color),
	 	refrigerador(Color,Lugar),Refrigeradores),write('Son:'), length(Refrigeradores,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Refrigeradores);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Refrigeradores);writeln('No hay'))).

	 lista_refrigeradores_en(Lugar):-
	 findall(('Hay un refrigerador de color',Color,'en',Lugar),
	 	refrigerador(Color,Lugar),Refrigeradores),
		write('Son:'), length(Refrigeradores,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Refrigeradores);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Refrigeradores);writeln('No hay'))).	


	lista_lavabos_en(Lugar):-
	 findall(('Hay un lavabo de color',Color,'de tipo',Tipo,'en',Lugar),
	 	lavabo(Color,Tipo,Lugar),Lavabos),write('Son:'), length(Lavabos,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Lavabos);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Lavabos);writeln('No hay'))).

	lista_lavabos_de_tipo(Tipo):-
	 findall(('Hay un lavabo de color',Color,'en',Lugar,'de tipo',Tipo),
	 	lavabo(Color,Tipo,Lugar),Lavabos),write('Son:'), length(Lavabos,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Lavabos);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Lavabos);writeln('No hay'))).	

	 lista_lavabos_de_color(Color):-
	 findall(('Hay un lavabo de tipo',Tipo,'en',Lugar,'de color',Color),
	 	lavabo(Color,Tipo,Lugar),Lavabos),write('Son:'), length(Lavabos,Longitud), writeln(Longitud),
	 	(Longitud is 1 -> writeln('La cual es: '),mostrarlista(Lavabos);
	 	(Longitud > 1 -> writeln('Las cuales son: '), mostrarlista(Lavabos);writeln('No hay'))).

% Booleano de existencia de un objeto en un lugar, recibe un objeto 
% (cuyos atributos pueden ser variables o no para conocer caracteristicas del primer objeto existente), 
% escrito en forma de predicado exeptuando el campo de Lugar/Ubicacion. 
% Ej: existe_mesa_en( Objeto, Lugar ) -> existe_mesa_en( mesa(blanco,rectangular), sala )

	existe_mesa_en(Objeto,Lugar):-
		findall(mesa(Color,Forma,Material),mesa(Color,Forma,Material,Lugar),Mesas),
		(existe(Objeto,Mesas) -> 
			writeln('Si existe. '), write('Son:');
		writeln('No existe') ).

	existe_sofa_en(Objeto,Lugar):-
		findall(sofa(Color,Forma),sofa(Color,Forma,Lugar),Sofas), 
		(existe(Objeto,Sofas) -> 
			writeln('Si existe. ');
		writeln('No existe')).

	existe_tele_en(Objeto,Lugar):-
		findall(television(Tipo),television(Tipo,Lugar),Teles), 
		(existe(Objeto,Teles) -> 
		 	writeln('Si existe. ');
		writeln('No existe')).

	existe_silla_en(Objeto,Lugar):-
		findall(silla(Color, Material),silla(Color, Material, Lugar),Sillas), 
		(existe(Objeto,Sillas) -> 
			writeln('Si existe. ');
		writeln('No existe')).	
	
	existe_lampara_en(Objeto,Lugar):-
		findall(lampara(Tipo,Forma),lampara(Tipo,Forma,Lugar),Lamparas),
		(existe(Objeto,Lamparas) -> 
			writeln('Si existe. ');
		writeln('No existe')).

	existe_cama_en(Objeto,Lugar):-
		findall(cama(Tipo),cama(Tipo,Lugar),Camas), 
		(existe(Objeto,Camas) -> 
			writeln('Si existe. ');
		writeln('No existe')).	

	existe_espejo_en(Objeto,Lugar):-
		findall(espejo(Tamano),espejo(Tamano,Lugar),Espejos), 
		(existe(Objeto,Espejos) -> 
			writeln('Si existe. ');
		writeln('No existe')).

	existe_pintura_en(Objeto,Lugar):-
		findall(pintura(Tamano,Imagen),pintura(Tamano,Imagen,Lugar),Pinturas),
		(existe(Objeto,Pinturas) -> 
			writeln('Si existe. ');
		writeln('No existe')).

	existe_maceta_en(Objeto,Lugar):-
		findall(maceta(Tamano),maceta(Tamano,Lugar),Macetas),
		(existe(Objeto,Macetas) -> 
			writeln('Si existe. ');
		writeln('No existe')).

	existe_florero_en(Objeto,Lugar):-
		findall(florero(Tamano),florero(Tamano,Lugar),Floreros),
		(existe(Objeto,Floreros) -> 
			writeln('Si existe. ');
		writeln('No existe')).

	existe_horno_en(Objeto,Lugar):-
		findall(horno(Color, Tipo),horno(Color, Tipo, Lugar),Hornos), 
		(existe(Objeto,Hornos) -> 
			writeln('Si existe. ');
		writeln('No existe')).

	existe_retrete_en(Objeto,Lugar):-
		findall(retrete(Color),retrete(Color,Lugar),Retretes), 
		(existe(Objeto,Retretes) -> 
			writeln('Si existe. ');
		writeln('No existe')).

	existe_regadera_en(Objeto,Lugar):-
		findall(regadera(Color),regadera(Color,Lugar),Regaderas), 
		(existe(Objeto,Regaderas) -> 
			writeln('Si existe. ');
		writeln('No existe')).
	
	existe_tapete_en(Objeto,Lugar):-
		findall(tapete(Color, Tamano),tapete(Color, Tamano, Lugar),Tapetes), 
		(existe(Objeto,Tapetes) -> 
			writeln('Si existe. ');
		writeln('No existe')).

	existe_ventana_en(Objeto,Lugar):-
		findall(ventana(Tamano),ventana(Tamano,Lugar),Ventanas), 
		(existe(Objeto,Ventanas) -> 
			writeln('Si existe. ');
		writeln('No existe')).

	existe_relog_en(Objeto,Lugar):-
		findall(relog(Color, Tamano),relog(Color, Tamano, Lugar),Relogs), 
		(existe(Objeto,Relogs) -> 
			writeln('Si existe. ');
		writeln('No existe')).	

	existe_gabinete_en(Objeto,Lugar):-
		findall(gabinete(Color, Tamano),gabinete(Color,Tamano,Lugar),Gabinetes), 
		(existe(Objeto,Gabinetes) -> 
			writeln('Si existe. ');
		writeln('No existe')).	

	existe_refrigerador_en(Objeto,Lugar):-
		findall(refrigerador(Color),refrigerador(Color,Lugar),Refrigeradores), 
		(existe(Objeto,Refrigeradores) -> 
			writeln('Si existe. ');
		writeln('No existe')).		

	existe_lavabo_en(Objeto,Lugar):-
		findall(lavabo(Color, Tipo),lavabo(Color,Tipo,Lugar),Lavabos), 
		(existe(Objeto,Lavabos) -> 
			writeln('Si existe. ');
		writeln('No existe')).
		

% Herramientas
	% Muestra el listado de una lista renglon por renglon 
		mostrarlista([]):- !. % Caso Base
			mostrarlista([C|Lista]):- write(C),nl,mostrarlista(Lista).

	% Booleano que represeinta si un elemento es parte de una lista
		existe(X, [Y|T]) :- X = Y ; existe(X, T).


