# Despliegue de Aplicación con WordPress y MySQL usando Kubernetes y Helm

## Descripción del Proyecto

En este proyecto, he desplegado una aplicación WordPress con una base de datos MySQL utilizando Kubernetes y Helm. El proceso comenzó con la creación del clúster y posteriormente transformé la configuración en un Chart de Helm. Esto requirió reestructurar varios componentes y generar templates, junto con una serie de modificaciones para garantizar el correcto despliegue.

## Estructura del Proyecto

```
my-helm-chart/
├── Chart.yaml
├── values.yaml
└── templates/
    ├── mysql-deployment.yaml
    ├── pv.yaml
    ├── pvc.yaml
    ├── wordpress-deployment.yaml
    └── wordpress-ingress.yaml
```

## Pasos Realizados

1. **Inicialización del Clúster**  
   Inicié Minikube con tres nodos, aunque durante el desarrollo comprobé que con dos nodos era suficiente.

2. **Preparación del Entorno**  
   - Creé una carpeta para almacenar el proyecto.
   - Definí un *namespace* llamado `kuberkid` donde se recrearán todos los recursos.

3. **Gestíon de Secretos**  
   - Generé los *secrets* necesarios para el despliegue de WordPress y MySQL.
   - Incorporé estos *secrets* en las configuraciones de los deployments correspondientes.

4. **Configuración de Servicios**  
   - Configuré los servicios necesarios para la comunicación entre los pods.
   - Utilicé `NodePort` para exponer WordPress y `ClusterIP` para MySQL.

5. **Verificación de MySQL**  
   - Verifiqué que MySQL estuviera corriendo correctamente.
   - Asigné privilegios al usuario `sergio` para gestionar la base de datos.

6. **Almacenamiento Persistente**  
   - Creé un *PersistentVolume* (PV) y un *PersistentVolumeClaim* (PVC).
   - Monté el volumen en el deployment y comprobé su correcta construcción.

7. **Pruebas de Funcionamiento**  
   - Realicé pruebas para asegurar que la aplicación funcionara correctamente.

8. **Probes de Salud**  
   - Configuré `livenessProbe` y `readinessProbe` utilizando `tcpSocket` para monitorear la salud de la aplicación.

9. **Exposición de la Aplicación**  
   - Activé *Ingress* para exponer la aplicación al exterior.

10. **Construcción del Chart de Helm**  
    - Con todos los archivos configurados, construí un Chart de Helm para facilitar el despliegue de la aplicación.

## Herramientas Utilizadas

- **Mobaxterm**: Para la gestión de conexiones y terminal.
- **Visual Studio Code**: Para la edición y gestión del código.

## Conclusión

El despliegue de WordPress y MySQL utilizando Kubernetes y Helm ha permitido automatizar y simplificar el proceso. La transformación en un Chart de Helm facilita futuras implementaciones y mejoras en la aplicación.
