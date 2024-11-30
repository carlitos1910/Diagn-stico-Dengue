%Hechos 
sintoma(fiebre).
sintoma(dolor_muscular).
sintoma(dolor_articular).
sintoma(dolor_de_cabeza).
sintoma(dolor_abdominal).
sintoma(sarpullido).
sintoma(nauseas).

% Reglas para el diagnóstico del dengue
% Para que se considere un posible caso de dengue, se deben cumplir ciertos síntomas
dengue(Sintomas) :- 
    member(fiebre, Sintomas),
    member(dolor_muscular, Sintomas),
    member(dolor_articular, Sintomas),
    member(dolor_de_cabeza, Sintomas).

% Diagnóstico de dengue leve
dengue_leve(Sintomas) :- 
    dengue(Sintomas),
    \+ member(dolor_abdominal, Sintomas),
    \+ member(sarpullido, Sintomas).

% Diagnóstico de dengue grave
dengue_grave(Sintomas) :- 
    dengue(Sintomas),
    member(dolor_abdominal, Sintomas),
    member(sarpullido, Sintomas).

% Regla para consultar el diagnóstico
diagnosticar(Sintomas) :-
    (dengue_grave(Sintomas) -> 
        write('Diagnóstico: Posible dengue grave.'),
        nl;
        dengue_leve(Sintomas) -> 
            write('Diagnóstico: Posible dengue leve.'),
            nl;
            write('Diagnóstico: No se sugiere dengue.')).
%Rama 1
git checkout -b base_sintomas
% hechos.pl
% Hechos 
sintoma(fiebre).
sintoma(dolor_muscular).
sintoma(dolor_articular).
sintoma(dolor_de_cabeza).
sintoma(dolor_abdominal).
sintoma(sarpullido).
sintoma(nauseas).
git add hechos.pl
git commit -m "Agregar hechos de síntomas"
git push origin base_sintomas
%Rama 2
git checkout -b diagnosticos
% diagnosticos.pl
% Reglas para el diagnóstico del dengue
% Para que se considere un posible caso de dengue, se deben cumplir ciertos síntomas
dengue(Sintomas) :- 
    member(fiebre, Sintomas),
    member(dolor_muscular, Sintomas),
    member(dolor_articular, Sintomas),
    member(dolor_de_cabeza, Sintomas).

% Diagnóstico de dengue leve
dengue_leve(Sintomas) :- 
    dengue(Sintomas),
    \+ member(dolor_abdominal, Sintomas),
    \+ member(sarpullido, Sintomas).

% Diagnóstico de dengue grave
dengue_grave(Sintomas) :- 
    dengue(Sintomas),
    member(dolor_abdominal, Sintomas),
    member(sarpullido, Sintomas).
    git add diagnosticos.pl
git commit -m "Agregar reglas para diagnóstico del dengue"
git push origin diagnosticos
%Ramas 3
git checkout -b consulta
% consulta.pl
% Regla para consultar el diagnóstico
diagnosticar(Sintomas) :-
    (dengue_grave(Sintomas) -> 
        write('Diagnóstico: Posible dengue grave.'),
        nl;
        dengue_leve(Sintomas) -> 
            write('Diagnóstico: Posible dengue leve.'),
            nl;
            write('Diagnóstico: No se sugiere dengue.')).
            git add consulta.pl
git commit -m "Agregar consulta para diagnóstico"
git push origin consulta


            


