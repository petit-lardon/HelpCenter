Tous les composants React ont une propriété props.
C'est un objet javascript qui contient tous les attributs passés par le composant parent.

## Passer des valeurs
Quand on appelle un composant, on peut passer des valeurs enregistrées dans le state pour dynamiser l'affichage.

    { this.state.counters.map(counter => (
        <Counter key={counter.id} value={counter.value} selected=true id={counter.id} />
    )) }
    value, selected et id seront des attributs de la propriété props du composant appelé (Counter)
    key, quant à lui est un mot clé réservé et ne sera pas un attribut


## Passer du DOM supplémentaire
Parfois, il est nécessaire de passer du DOM en plus dans le composant enfant.
Par exemple, on veut ajouter un titre dynamiquement au composant enfant

    On doit alors utiliser dans balises ouvrantes / fermantes sur l'appel du composant
    { this.state.counters.map(counter => (
        <Counter key={counter.id} value={counter.value}>
            <h3>Counter {counter.id}</h3>
        </Counter
    )) }
    
Dans le composant enfant, la propriété props a alors un attibut supplémentaire ``children``

    props = {
        value: X,
        children: {Reat.element}
    }
    
    On peut l'utiliser ainsi dans le rendre du composant
    {this.props.children}
