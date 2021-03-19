# La propriété state
La propriété state est une propriété de base des composants React
C'est un objet qui contient toutes les données nécessaires au bon fonctionnement du composant

On peut appeler directement ses données dans le retour jsx
    
    { this.state.field }
    
La propriété state peut être mise à jour dans le code et être rendue automatiquement à l'écran

## La détection du changement
Dans la classe Component, une méthode existe et va nous permettre de mettre à jour le state facilement
``setState()``

Dans cette fonction, on passe en paramètre uniquement la partie du state que l'on veut mettre à jour.

    this.setState({ count: this.state.count + 1 });
    grace à cette méthode setState, React est au courant du changement d'état et l'affichage se et à jour
    



