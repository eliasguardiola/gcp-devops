# Apuntes

## Sprint 1 - levantar app de python con git

- Crear repositorio de Github
- Hacer un commit del readme
- Proteger el branch main contra escritura (en settings) (primero hay que pushear un commit)
- Usar otros branches para hacer cambios en el main, debe haber pull request antes

## Usar otros branches para OR
`git checkout -b "feature/task-02"`
`git push origin feature/task-02`

## Crear imagen de docker basada en Dockerfile
`docker build --tag python-docker-image .`

## Hacer rebuild de la imagen
`docker build --tag python-docker-image .`

## Levantar imagen
`docker run -p 5001:5000 python-docker-image`

## Budget
Definir alarmas de budget

## Activar GKE
Hacerlo cluster con configuracion manual

## Codebuild
Nos va a servir para compilar las imagenes de docker y luego desplegarlas a kubernetes

## Codebuild
- Buscar  "Cloud Build" y activarla
- Buscar de nuevo "Cloud Build" e ir al dashboard
- Ir a triggers y "Connect Repository"
- Nos va a pedir installar Google Cloud Build
- Loguearnos en Github y darle permisos solo a nuestro repo devops
- No hacer trigger por ahora
- Crear trigger con el repositorio
- En el eventro "Push to branch"
- En Configuration poner "Cloud Build configuration file"
- Crear yaml de cloudbuild.yaml
- Hacer PR a main
- Despues del merge ya se habra corrido el build
- Revisar si corrio bien
- Revisar buscando "Artifact Registry" para ver si se subieron las imagenes

## GKE
- Crear namespace `kubectl create namespace gcp-devops-prod`
- Crear `gke.yaml` con el deployment para K8S
- Editar `cloudbuild.yaml`con tareas para compilar imagen, pushear y desplegar en GKE
- Merge a main
- Revisar que se desplego el deployment correctamente
- Crear servicio para exponer puerto del pod, en el `gke.yaml`
- Crear otro branch "development"
- Editar cloudbuild.yaml para que el build, push de las imagenes sean para `gcr.io/$PROJECT_ID/gcpdevops-dev` y el namespace para `gcp-devops-dev`
- Tambien editar el `gke.yaml` para que apunte a la imagen dev y namespace dev