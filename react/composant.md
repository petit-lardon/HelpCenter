# La base d'un composant

    import React, { Component } from "react";
    
    class ... extends Component {
        state = {};
    
        render() {
            return (
    
            );
        }
    }
    
    export default ...;

## L'import / export
Une classe peut être utilisée dans tout le projet, à condition qu'elle soit exportée et importéelà où l'on veut l'utiliser

    En bas de la classe
    export default MyClass;
    
    En haut de la classe qui l'utilise
    import MyClass from "./chemin"

## La propriété state
La propriété state est une propriété de base des composants React
C'est un objet qui contient toutes les données nécessaires au bon fonctionnement du composant

On peut appeler directement ses données dans le retour jsx
    
    { this.state.field }
    
## L'utilisation d'une fonction
On peut également appeler une fonction du composant
    
    { this.myFunction() }

## Le render
La classe React a obligatoirement une fonction render qui se chargera d'afficher le contenu sur notre page

La fonction render renvoi systématiquement un objet jsx qui sera compilé par la suite

## L'appel de composant
Dans un composant on peut appeler d'autres composants et les afficher

    <MonComposant />
    <MonComposant>...</MonComposant>
    
Chaque composant appeleé sera indépendant des autres, même si 2 composants du même type sont appelés.
On peut même boucler sur un élément du state pour générer plusieurs composants

    class Counters extends Component {
        state = {
            counters: [
                {id: 1, value: 0},
                {id: 2, value: 0},
                {id: 3, value: 0}
            ]
        }
        
        render() {
            return (
                <React.Fragment>
                    { this.state.counters.map(counter => <Counter key={counter.id} value={counter.value} />) }
                </React.Fragment>
            )
        }
    }
