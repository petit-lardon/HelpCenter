# Rappels EcmaScript

## Var, let, const
En javascript, les variables sont déclarées via le mot clé `var`
Le soucis est alors que la variable est disponible dans tout l'objet dans lequel elle est déclarée

Deux mots clés ont été ajoutés pour déclarer des variables. La variable est alors disponible uniquement dans le bloc (boucle, fonction, ...) dans lequel elle a été déclarée
    
    let
    const
    
Le mot clé const permet de définir une constante, la variable ainsi créée ne sera pas modifiable par la suite

## Le spread opérateur
Le spread opérateur est une fonction qui permet de copier des données simplement et rapidement
La donnée copiée sera identique et complètement indépendante

Cette fonction est représentée par ``...``

On peut l'utiliser pour différentes raisons

    Copier un tableau
    let newArray = [...myArray]
    
    Eclater une chaine de caractère en tableau
    let stringArray = [...myString]
    
    Concaténer plusieurs tableaux
    let newArray = [...array1, ...array2]
    
    Concaténer plusieurs objets et ajouter de nouvelles propriétés
    const newObj = {...obj1, 'property': 'value', ...array2}

## La déstructuration
La destructuration permet de déclarer toutes les entrées (souhaitées) d'un objet dans des variables rapidement

    On aurait tendance à faire
    const street = address.street
    const city = address.city
    const country = address.country
    
    En desctructurant
    const {street, city, country} = address
    
    On peut choisir les données souhaitées
    const {street, country} = address
    
    On peut choisir définir un alias
    const {street: st} = address
    
La destructuration vient chercher l'élément dans l'objet qui a le même nom que la variable définie

##La méthode .findIndex()
Cette fonction permet de trouver la position d'un élément en particulier dans un tableau particulier

    clients.findIndex(function(client) {
        return client.id === id;
    });
    
    Equivaut à 
    clients.findIndex(client => client.id === id);

## La méthode .splice()
Cette fonction permet de retirer des éléments d'un tableau à partir d'un index donné

    clients.splice(index, 1);

## accéder à un élément du DOM
En React, on n'accède pas à un élément du DOM en utilisant l'objet document de javascript.

Pour une meilleur maintenance des composants, on utilise des références directement dans la classe.

    class SubmitForm extends Component {
        username = React.createRef();
        
        //on peut accéder aux donées ainsi
        this.username.current.value;
        
        render() {
            return <input ref={this.username} id='username' type='text'>
        }
    }

L'utilisation de refs est utile si l'on souhaite mettre une animation sur un élément ou modifier des focus.
Mais il ne faut pas en abuser.
