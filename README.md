Spree::EnhancedRelation
-----------------------
* adiciona cuatro clases herederas de Spree::RelationType
  - RelationTypeOneToOne
  - RelationTypeOneToMany
  - RelationTypeManyToOne
  - RelationTypeManyToMany (esta es la por defecto)

* aparecen 4 botones
  - Adicionar one to one relation
  - Adicionar one to many relation
  - etc.

* permite definir (esto creo que ya lo hace pero hay que revisar) related-to y relatable con herederos de Spree::Product

* en la vista de administracion, cuando se esta creando una nueva relacion
  se especifica el tipo del padre y el tipo del hijo

* la idea es que RelationType{p1}To{p2} valide
  - que en el relatable se cumpla p1
  - que en el related-to se cumpla p2

* adiciona a la clase un atributo main
  - el valor por defecto es false
  - solo puede haber un producto relacionado con la relacion que sea el main

* implementa un position [esto no se si ya lo tiene]
  - es para definir un orden entre los elementos relacionados

* implementa los metodos en la clase product
  - i_am_related_to_this_product(nombre_de_relation) --> one_to_one
  - this_product_is_related_to_me(nombre de la relacion)
  - those_products_are_related_to_me(nombre) --> para los one_to_many (children)
  - get_related(nombre_de_relation) que con el nombre de la relacion infier el tipo y devuelve array o individual


* en la vista de admin cuando se crea una relacio se especifica el tipo (1-1, 1-m, m-1)

* en la vista de admin se define que tipo es el relatable y que tipo es el related-to

* cuando se va a relacionar un producto con otro sucede lo siguiente
  - se mira a ver de que tipo es el producto
  - se muestran las relaciones que tienen relatable de tipo igual al producto
  - cuando se escoje una relacion solo se dan a escoger productos del tipo del related-to de la relacion

* cuando se le dice a un producto.get-related(relation-name) [esto no se si vale la pena o no]
  - se busca el tipo de relateable y related-to de esa relacion
  - primero se busca si product es del tipo relatable y se buscan todos los related-to
  - luego se busca si el product es del tipo related-to y se buscan los relatables
