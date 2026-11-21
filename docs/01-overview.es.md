# Resumen

[English](01-overview.md)

La app pública se encarga del descubrimiento, la consulta de destinos y los favoritos locales. El panel admin gestiona alojamientos, disponibilidad, contactos, usuarios y perfil. Ambos clientes consumen un solo contrato de API.

La API aplica el alcance por propietario, decide qué se muestra en el catálogo y procesa imágenes. MongoDB guarda los datos del producto y Cloudflare R2 almacena las imágenes procesadas.

[Arquitectura](02-architecture.es.md)
