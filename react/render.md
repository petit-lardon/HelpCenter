# Le render
La classe React a obligatoirement une fonction render qui se chargera d'afficher le contenu sur notre page

Lorsque l'ont fait un return, le javascript attend une instruction juste après le mot clé.
S'il n'y en a pas, ce sera considéré comme un retour vide.
La solution est d'encapsuler le retour complet dans des parenthèses
    
    return (
        ...
    );

## Retour simple
La fonction render renvoi systématiquement un seul objet jsx qui sera compilé par la suite

    return <h1>Title</h1>
    
## Retour complexe
Un élémenent du DOM est considéré comme un objet jsx. Si l'on souhaite en retourner plusieurs, il faut encapsuler le tout dans un objet unique (souvent une div simple)

    return (
        <div>
            <h1>{ state.content.title }</h1>
            <p>{ state.content.description }</p>
        </div>
    );

Le soucis est qu'une div vide sera ajoutée au DOM de l'application

## Fragment
Si on ne veut pas voir la div vide, on peut encapsuler dans un objet React

    return (
        <React.Fragment>
            <h1>{ state.content.title }</h1>
            <p>{ state.content.description }</p>
        </React.Fragment>
    );
