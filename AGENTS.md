# modo-playa-platform

## Contexto de trabajo

Si existe un workspace con AGENTS.md en los directorios padre, leerlo explícitamente antes de editar y seguir sus referencias. Una raíz Git anidada puede impedir la herencia automática. Fuera de ese entorno, este archivo y el README deben ser suficientes para trabajar.

## Alcance y fuentes

- Repositorio de documentación de arquitectura; no contiene el runtime del producto.
- README presenta límites y repositorios participantes; docs/ desarrolla overview y arquitectura.
- diagrams/ contiene material visual y referencias a sus fuentes.
- Confirmar contratos en los repositorios de implementación antes de cambiar relaciones.
- El sitio portfolio mantiene las fuentes de diagramas del ecosistema.
- Conservar nombres de componentes y límites de ownership coherentes con código.

## Edición y verificación

- Mantener alineadas las versiones inglés/español de documentación técnica.
- Verificar enlaces Markdown locales después de mover o renombrar archivos.
- Mantener especificación, HTML, PNG y manifest juntos cuando corresponda regenerar.
- No regenerar diagramas por una edición de texto que no modifica su contenido.
- No hay build/test de aplicación: usar las herramientas reales indicadas en diagrams/README.

## Restricciones

- No añadir handlers, servicios, infraestructura desplegable ni copias de código de otros repos.
- Referenciar fuentes técnicas actuales sin duplicar sus README.
- Distinguir componentes lógicos e implementaciones intercambiables de una misma API.
- No inferir despliegues o comportamiento productivo a partir de un diagrama.
- Mantener el repo utilizable sin acceso a documentación de un workspace personal.
