# Apuntes

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