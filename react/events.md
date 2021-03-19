# Les évènements

Sur certains éléments du DOM, on peut executer des fonctions en fonction des évènements

Les évènements React sont les mêmes évènements qu'en HTML mais sont appelés en ``camelCase``

En React, on ne peut pas envoyer ``false`` pour empêcher le comportement par défaut.
Il faut impérativement appeler le ``preventDefault``

    <a href="#" onclick="console.log('Le lien a été cliqué.'); return false">
      Clique ici
    </a>
    
    En React
    function ActionLink() {
      function handleClick(e) {
        e.preventDefault();
        console.log('Le lien a été cliqué.');
      }
    
      return (
        <a href="#" onClick={handleClick}>
          Clique ici
        </a>
      );
    }


## Référence à la fonction
Par convention, les fonctions liées à un évènement sont appelées dans la classe en commencant par ``handle``.

Dans l'évènement, on appelle une référence à la fonction et non la fonction directe
    
    <button onClick={this.handleClick}></button>
    Si on met l'appel à la fonction ( this.handleClick() ), elle serait appelée automatiquement


## this dans la fonction
Quand on lie une fonction à un évènement, le this dans la fonction ne représente pas l'objet global.

Il faut impérativement lier le this (objet courant) à la référence de la fonction.
3 possibilités

    le bind dans la référence à la fonction
    {this.handleClick.bind(this)}
    
    la fonction fléchée (ne perd pas le this)
    {() => this.handleClick()}
    dans ce cas, on met bien les parenthèses
    
    laisser la référence à la classe 
    {this.handleClick}
    déclarer la fonction en tant que fonction fléchée
    handleClick = () => {}

Dans le dernier exemple, handleClick devient une propriété de l'objet qui contient une fonction fléchée.
Le contexte n'est pas perdu, le this est bien reconnu


## Le passage de paramètres
Lorsque l'on ajoute un évènement, il est souvent nécessaire d'ajouter des paramètres à la fonction
Or nous ne pouvons pas ajouter les paramètres comme en javascript, il n'y a pas d'appel de fonction mais plutôt une référence à la fonction

    A NE SURTOUT PAS FAIRE
    <button onClick={this.handleClick(id)}>

Il faut donc modifier l'appel de la référence à un appel de fonction en utilisant la fonction fléchée
    
    <button onClick={() => this.handleClick(id)}>


## La gestion des events entre parent et enfant
Parfois, on doit ajouter des evenements sur un composant pour effectuer une action.
Mais il arrrive que dans le composant, le state ne comporte que des données pour l'affichage.
C'est le parent qui initialise le composant enfant

    Notre composant Counters appelle plusieurs composants Counter
    Le Counter ne s'occupe que de son affichage
    
    class Counters extends Component {
        state = {
            counters: [
                {id: 1, value: 4},
                {id: 2, value: 0}
            ]
        }
    }
    
    class Counter extends Component {
        state = {
            value: this.props.value
        }
    }

Si on veut supprimer un compteur, le bouton sera placé au niveau de l'affichage du Counter mais la fonction de suppression devra obligatoirement se placer sur le composant qui initialise les compteurs.

    Counter
    <button onClick={() => this.props.onDelete({this.props.id)}></button>
    
    Counters
    render => <Counter key={counter.id} value={counter.value} onDelete={this.handleDelete} />
    this.handleDelete = (id) => {
        const counters = this.state.counters.filter(c => c.id !== id);
        this.setState({counters: counters});
    }
    
Par convention, dans la classe parent, on écrit la fonction ``handleAction``, qu'on fait référence dans l'appel du composant enfant par ``onAction``.
Dans la classe enfant, on appelle la propriété ``onAction`` de props.


