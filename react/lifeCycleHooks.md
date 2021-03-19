Chaque composant hérité de Component contient différentes fonctions qui sont automatiquement appelées en fonction de l'état de vie du composant.

Voici les plus courantes:


## Gestion des erreurs
Ces méthodes sont appelées lorsqu'une erreur survient dans n'importe quel composant enfant lors de son rendu:
1. static getDerivedStateFromError()
2. componentDidCatch()


## Déclaration du composant

Les méthodes sont appelées automatiquement dans cet ordre: 
1. constructor()
2. static getDerivedStateFromProps()
3. render()
4. componentDidMount()

### Constructor
L'appel du constructeur n'est pas obligatoire. 
Si on implémente le constructeur, il faut impérativement passer la variable ``props``

    constructor(props) {
        super(props);
    }

Les constructeurs React sont habituellement utilisés pour deux raisons: 
1. Initialiser l'état local (LifeCycleHooks) en affectant un objet à ``this.state``
2. Lier des méthodes gestionnaires d'évènements à l'instance


Il est interdit d'appeler la fonction ``setState()`` dans le constructeur.
Il faut affecter l'état initial directement à ``this.state``

    constructor(props) {
        super(props);
        this.state = { counter: 0 };
        this.handleClick = this.handleClick.bind(this);
    }

Le constructeur est le seul endroit où il faut affecter une valeur à state en déclarant this.state directement.


### Render
La méthode ``render()`` est la seule méthode requise au sein du composant.

La fonction render doit être pure, 
1. elle ne doit rien changer à l'état local du composant
2. elle doit renvoyer le même type de résultat à chaque fois
3. ne doit pas interagir directement avec le navigateur


### ComponentDidMount
Cette méthode est appelée juste après le constructeur.
C'est ici que l'on peut faire des requêtes ajax pour mettre à jour le state depuis le serveur.

Cette fonction est appelée quand le composant est présent dans le DOM.

## Mise à jour du composant

Les méthodes sont appelées automatiquement dans cet ordre: 
1. static getDerivedStateFromProps()
2. shouldComponentUpdate()
3. render()
4. getSnapshotBeforeUpdate()
5. componentDidUpdate()


    componentDidUpdate(prevProps, prevState) {
        console.log('prevProps', prevProps);
        console.log('prevState', prevState);
        
        if(prevProps.counter.value !== this.props.counter.value) {
            //ajax call and get new data from the server
        }
    }


## Suppression du composant

Une méthode est appelée automatiquement: 
1. componentWillUnmount()

Elle est appelée juste avant que le composant ne soit supprimé du DOM.


