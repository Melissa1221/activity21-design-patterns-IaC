



# Builder
`InfrastructureBuilder` orquesta Factory ->Prototype -> Composite y genera un JSON mediante la combinacion  de `NullResourceFactorry.create(...)` el cual crea un diccionario con la estrutura minima de terraform esperado para un `null_resource`, luego usa prototype para realizar una copia profunda y se le aplica una funcion mutadora que modifica los nombres de cada clave  y le agrega su indice correspondiente y la mutacion gartantiza que cada indice tenga un nombre unico, luego con Composite, cada clon resultante se añade al CompositeModule, que va acumulando todos los bloques bajo la clave "resource". Finalmente, al invocar export(path), se fusionan esos fragmentos en un único diccionario y se escribe el archivo .tf.json listo para que Terraform lo consuma.