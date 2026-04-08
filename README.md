; ============================================================
; SISTEMA EXPERTO: DIAGNÓSTICO MÉDICO DE LA DIABETES
; ============================================================
; ============================================================
; SECCIÓN 1: PLANTILLAS DE HECHOS (deftemplates)
; ============================================================
(deftemplate paciente
    "Información básica del paciente"
    (slot nombre      (type STRING))
    (slot edad        (type INTEGER) (default 0))
    (slot sexo        (type SYMBOL)  (default desconocido)) ; masculino / femenino
    (slot peso        (type FLOAT)   (default 0.0))         ; kg
    (slot talla       (type FLOAT)   (default 0.0))         ; metros
    (slot imc         (type FLOAT)   (default 0.0)))        ; calculado
(deftemplate laboratorio
    "Resultados de laboratorio del paciente"
    (slot nombre               (type STRING))
    (slot glucosa-ayunas       (type FLOAT) (default 0.0))  ; mg/dL
    (slot glucosa-postprandial (type FLOAT) (default 0.0))  ; mg/dL (2h post)
    (slot glucosa-aleatoria    (type FLOAT) (default 0.0))  ; mg/dL
    (slot hba1c                (type FLOAT) (default 0.0))  ; porcentaje
    (slot tolerancia-glucosa   (type FLOAT) (default 0.0))) ; mg/dL (PTOG 2h)
(deftemplate sintomas
    "Síntomas reportados por el paciente"
    (slot nombre         (type STRING))
    (slot poliuria       (type SYMBOL) (default no)) ; si / no
    (slot polidipsia     (type SYMBOL) (default no))
    (slot polifagia      (type SYMBOL) (default no))
    (slot fatiga         (type SYMBOL) (default no))
    (slot vision-borrosa (type SYMBOL) (default no))
    (slot perdida-peso   (type SYMBOL) (default no))
    (slot heridas-lentas (type SYMBOL) (default no)))
(deftemplate historial
    "Antecedentes médicos del paciente"
    (slot nombre                 (type STRING))
    (slot antecedentes-familiares (type SYMBOL) (default no)) ; si / no
    (slot hipertension           (type SYMBOL)  (default no))
    (slot enfermedades-previas   (type STRING)  (default "ninguna"))
    (slot medicamentos           (type STRING)  (default "ninguno"))
    (slot alergias               (type STRING)  (default "ninguna")))
(deftemplate riesgo
    "Nivel de riesgo calculado para el paciente"
    (slot nombre (type STRING))
    (slot nivel  (type SYMBOL))) ; bajo / moderado / alto / muy-alto
(deftemplate diagnostico
    "Resultado del diagnóstico del sistema"
    (slot nombre     (type STRING))
    (slot resultado  (type STRING))
    (slot confianza  (type SYMBOL))) ; alta / media / baja
(deftemplate recomendacion
    "Recomendaciones generadas por el sistema"
    (slot nombre      (type STRING))
    (slot tipo        (type STRING))
    (slot descripcion (type STRING)))
(deftemplate estado-sistema
    "Control del flujo de ejecución del sistema"
    (slot fase (type SYMBOL) (default inicio))) ; inicio / recoleccion / inferencia / resultado / fin
