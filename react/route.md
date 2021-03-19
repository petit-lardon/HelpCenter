Le système de route est à faire entièrement à la main.
React n'est qu'une librairie après tout.

Pour cela, il est nécessaire d'installer un composant dans le projet.

    npm install react-router-dom
    
Une fois installé, il faut encapsuler l'app globale par le composant ``<BrowserRouter />``

C'est un composant qui utilise l'API historique du navigateur. Dans tout notre composant encapsulé, on pourra utiliser l'historique de navigation.

## Déclarer une route 

### Appel d'un composant sans paramètre
Finalement, il faut enregistrer les routes, pour dire à React quel composant il faut afficher en fonction de la route.

    <div className="content">
        <Route path="/not-found" component={NotFound} />
        <Route path="/" exact component={Home} />
    </div>

React va lire l'URL et comparer au path du composant ``<Route />``.

Attention, pour la redirection, c'est tout ce qui commence par le path.

Le mot clé ``exact`` permet de dire 'je veux cette URL exactement'.

### Appel d'un composant en injectant des paramètres
On peut également créer une route pour afficher un composant particulier.
Le composant aura parfois besoin de paramètres pour fonctionner.

Il suffit juste de passer par la fonction render au lieu de l'appel du composant.
Il ne faut pas oublier depasser les props en paramètre ou ils seront supprimés.

    <Route path="/products" render={(props) => <Products sortBy="newest" {...props} />} />

## Le composant Switch

On peut contourner le souci d'url en encapsulant les routes et redirections par le composant ``<Switch />``

Ce composant permet de dire, dès qu'on a une correspondance entre l'URl et les données, on affiche la page et on ne regarde pas les autres routes.

    <div className="content">
      <Switch>
        <Route path="/products/:id" component={ProductDetails} />
        <Redirect from="/messages" to="/posts" />
        <Route path="/not-found" component={NotFound} />
        <Route path="/" exact component={Home} />
        <Redirect to="/not-found" />
      </Switch>
    </div>

Cela implique d'écrire les routes et redirections du plus spécifique au plus générique.

## Les liens

Quand on fait une navigation, on souhaite afficher du contenu en fonction de l'URL appelée.

Tout les principe de react est d'afficher du contenu et de recharger uniquement ce qui a été modifié.
Or, quand on fait un lien standard, on est redirigé vers une nouvelle URL, la page entière est donc rechargée.

    <a href="http://link">Link</a>
    
Tout le contenu de l'application se trouve dans des composants, tout est donc compilé ensemble dans le fichier js généré par React.

Au lien de faire un lien standard, il faut appeler un composant proposé par react-router-dom pour garder le système de refresh des composants et ainsi ne recharger que ce qui a été modifié.

    import {Link} from 'react-router-dom';
    
    const NavBar = () => {
        return <Link to="/myLink">Link</Link>;
    }


## La rediretion

React-router-dom propose d'autres fonctions dont une pour effectuer des redirections.

Lorsque l'on déclare des routes, on affecte généralement une route à la page 404.

    <Route path="/404" component={NotFound} />
    
Mais si on tente d'accéder à une URL qui n'existe pas, il faut penser à faire une redirection après la déclaration des différentes routes.

    <Redirect to="/404" />

On peut également effectuer une redirection pour une unique URL donnée.

    <Redirect from="/message" to="/post" />


## Navigation progammatique

Parfois, il est nécessaire de rediriger l'utilisateur vers une page après une action.

C'est notamment le cas après une soumission de formulaire. Au clic sur la soumission, on veut rediriger vers la page précédente.

    this.props.history.push('/products');
    
Dans ce cas, on redirige vers la page produit mais l'utilisateur pourra toujours revenir à la page précédente en cliquant sur la flèche dans le navigateur.

Mais parfois, on veut empêcher ce retour, notamment après une authentification (on ne veut pas que l'utilisateur puisse revenir sur le formulaire).
On va donc utiliser l'autre fonction du
    
    this.props.history.replace('/products');
