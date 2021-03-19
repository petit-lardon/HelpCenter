Un composant contient parfois uniquement une méthode render et n'a ni besoin de state ou de fonctions. 
Seule la variable props lui est nécessaire.

Dans ce cas, on peut convertir le composant en un composant fonctionnel.

Au lieu d'utiliser une classe, on utilise une unique fonction.

    class NavBar extends Component {
        render() {
            return ();
        }
    }
    
    transformé en
    const NavBar = () => {
        return ();
    }

Toutefois, dans les composants fonctionnels, ``this.props`` n'est pas reconnu.
Il faut lepasser en paramètre de la fonction et supprimer le ``this``

    class NavBar extends Component {
        render() {
            return ({this.props});
        }
    }
    
    transformé en
    const NavBar = (props) => {
        return ({props});
    }
