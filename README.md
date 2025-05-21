# 📝 Licenses Classfier

### Pasos que he seguido para llevar acabo la prueba tecnica:


1. **Leer la prueba tecnica y definir las tareas**  
   Primero lei y entendi lo que se pedia, con la ayuda de un bloc de notas fui listando las tareas, por ejemplo:
   -Crear los endpoints get licenses,get summary y put licenses
   -Crear el servicio para clasificar las licencias y generar los datos de salida
   -Crear el modelo de pydantic para la validacion de datos

2. **Configuracion del proyecto**  
   Una vez ya tenia el listado de tareas a hacer, defini la estructura de carpetas del proyecto,que fue:
   - `app/api/endpoints/`  
     Contiene los endpoints de la API.
   - `app/api`  
     Contiene el enrutador de toda la aplicacion. (`router.py`).
   - `app/config/`  
     Configuración global para las variables de entorno, actualmente solo para las api keys de openai y groq (`config.py`).
   - `app/data/`  
     Archivos de entrada y salida, y esquema JSON para el LLM (`input.xlsx`, `output.xlsx`, `licencias_schema.json`).
   - `app/requirements/`  
     Dependencias del proyecto (`requirements.in`).
   - `app/schemas/`  
     Definición de modelos de datos con Pydantic (`License.py`).
   - `app/services/`  
     Lógica de negocio  (`license_service.py`).
   - `app/tests/`  
     Pruebas automatizadas del proyecto (`test_licencias_router.py`).
   - `app/utils/`  
     Funciones auxiliares, como procesamiento de datos (`process_data.py`).
   - Archivos raíz:
     - `main.py`: Punto de entrada de la app.
     - `.env_template`: Variables de entorno de ejemplo.
     - `docker-compose.yml`: Configuración para entorno Docker.
     - `Dockerfile`: Imagen de Docker para la app.
     - `.gitignore`: Exclusiones de Git.
     - `pytest.ini`: Configuración de pytest.

3. **Desarrollo de funcionalidades**  
   Una vez ya cree la estructura del proyecto fui haciendo las tareas, que se basaban en:
   -Definicion de endpoints --> Genere las rutas mediante copilot,le dije: "Generame un router de Fastapi con los siguientes endpoints:Get Licenses,Get Summary y PUT License", una vez lo genero, cree el modelo License de Pydantic para que se validara la salida de los endpoints Get Licenses,y PUT License.
   -Definicion de servicios --> Mire la doc de openai,genere la api key y cogi el codigo de ejemplo que daba openai en la documentacion y le dije que lo modificara.
   -Cuando ya tenia todo, fui probando los enpoints y como tardaba, modifique Get Licenses para que ejecutara una "task" por cada item del excel, lo cual incremento el rendimiento, incluso fue mejor que implementar paralelizacion con concurrent.

4. **Pruebas**  
   Le explique a chatgpt lo que necesitaba y le puse como contexto los endpoints y como funcionaban cada enpoint, pasandole tambien el modelo de datos

5. **Docker**  
   Al crear los ficheros Dockerfile y docker-compose.yml,al haberlo echo tantas veces,me lo genero copilot,lo revise,cambie las rutas y variables de entorno,lo probe y funciono sin problemas.
