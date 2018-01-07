# Pré-requis 

Afin de pouvoir coder sur react-native, nous allons avoir besoin d'installer deux dépendances :  

- Le CLI (command line interface) de React Native
- L'application Expo sur notre device (iOS ou Android)

## Installer React-Native CLI 

Dans un terminal, entrez là commande suivante :  

`npm install -g create-react-native-app`

Le CLI va nous permettre de générer des projets React Native directement depuis le terminal !

## Installer Expo

Expo est une application mobile qui va nous permettre de tester notre application en temps réel.

- Lien pour [iOS](https://itunes.apple.com/app/apple-store/id982107779?ct=www&mt=8)
- Lien pour [Android](https://play.google.com/store/apps/details?id=host.exp.exponent&referrer=www)


### Voilà, nous sommes prêt pour commencer !

# DrawParty 

L'objectif de cette semaine va être de concevoir l'application DrawParty : un Pictionnary local sur portable. 

Pour cet exercice, vous n'aurez pas besoin de créer de nouveaux fichiers ou de navigation : l'intégralité de l'exercice peut se faire dans le ficher `App.js`

Nous découperons l'exercice en deux parties : une première partie qui consistera créer l'interface de dessin, puis une seconde ou nous créérons le jeu.

## L'interface de dessin

L'interface de dessin que nous allons créer comportera les fonctionnalités suivantes :

- Une zone de dessin
- Un color-picker de changer les couleurs du crayon
- Une liste de boutons qui permet de changer la taille de la pointe du crayon
- Un bouton pour annuler le dernier trait
- Un bouton pour effacer le canvas
- Un timer pour calculer le temps restant (qui tournera mais ne sera pas actif pour l'instant)
- Un bouton qui permet d'annoncer que le dessin a été trouvé


## Partie 1 : Le dessin
### 1. Créer le projet

**1.a Ouvrez un terminal et déplacez vous à l'aide de `cd` dans le dossier ou vous souhaitez installer cet exercice**

**1.b Une fois dans le dossier, lancez les commandes suivantes dans l'ordre :**

```
create-react-native-app DrawParty
cd DrawParty
npm start
```

🎉 Vous venez de créer votre premier projet React Native !

![Congrats](https://media0.giphy.com/media/g9582DNuQppxC/giphy.gif)


### 2. La zone de dessin
**2.a Installez [le component rn-draw](https://github.com/jayeszee/rn-draw) et importez-le dans le fichier `App.js`**

**2.b À l'aide de la démo présente dans la documentation de `rn-draw`, ajoutez le component `RNDraw` à l'interieur de la `View` parente du fichier `App.js`** 

> ✋ À cette étape, appelez-moi pour que je vienne vérifier votre code. Si tout s'est bien passé, vous devriez pouvoir déjà dessiner sur votre portable !
    
### 3. Le color picker
La fonctionnalité à développer ici est la possibilité de changer la couleur du crayon.

**3.1 Installez le component [react-native-color-wheel](https://github.com/netbeast/react-native-color-wheel) et importez le dans le fichier `App.js`**

**3.2 Modifiez le `render` du component `App` afin qu'il soit de la forme:**

```html
<View style={styles.container}>
    <View style={styles.drawContainer}>
        // Mettre RNDraw ici
    </View>
    <View style={styles.actionsContainer}>
        
    </View>
</View>
```

avec les styles suivant:
```js
const styles = StyleSheet.create({
    container: {
        flex: 1
    },
    drawContainer: {
        flex: 1
    },
    actionsContainer: {
        height: 170, 
        padding: 15
    }
})
```

**3.3 Ajoutez la color wheel dans la View `actionsContainer` (et changez le style du color picker pour que sa largeur et hauteur soient égales à 130)**

> ✋ À cette étape, appelez-moi pour que je vienne vérifier votre code. Si tout s'est bien passé, vous devriez pouvoir dessiner et voir la color wheel !


### Notre premier state : `color`
Avant de commencer cette partie, veuillez lire la [documentation du state.](https://facebook.github.io/react-native/docs/state.html). Le but de cette partie est de créer un state `color` qui variera en fonction de la color wheel, puis d'associer cette couleur à `rn-draw`


**3.4 À l'aide la documentation précédente, créez un `constructor` pour le component `App`**

**3.5 Dans le `constructor`, initialisez le state `color` avec une valeur de `#000000`**

**3.6 Dans la View `ActionsContainer`, affichez la valeur de la variable `color`**  
*⚠️ Attention pensez bien à importer `Text` de React Native !*

> ✋ À cette étape, appelez-moi pour que je vienne vérifier votre code. Si tout s'est bien passé, vous devriez voir `#000000` s'afficher !

**3.7 À l'aide de la fonction `setState` et de la props `onColorChange` de `react-native-color-wheel
`, faites en sorte que la couleur selectionnée sur la wheel s'affiche à la place de `#000000`**  

**3.8 Changez la couleur du crayon en utilisant la props `color` de `rn-draw`.**

> ✋ À cette étape, appelez-moi pour que je vienne vérifier votre code. Si tout s'est bien passé, vous pouvez maintenant changer la couleur du crayon.

🎉 Vous êtes officielement le maître de la couleur
![Congrats](https://media1.giphy.com/media/z0zTHzcwM4VYQ/giphy.gif)

### 4. La taille de la mine
Pour cette partie, copiez le tableau ci dessous avant la déclaration du component (`export default class [...]`)

```
const strokes = [2, 4, 6, 8, 10];
```

**4.1 Dans le `constructor`, initialisez un state `strokeWidth` à la valeur `4`**

**4.2 Modifiez le `Text` qui affiche la couleur afin qu'il affiche à présent la valeur de `strokeWidth`.**

**4.3 À l'aide de la fonction `map` de javascript et `Text` de `react-native`, affichez toutes les valeurs du tableau `strokes` dans la `View` `ActionsContainer`**

**4.4 Placez chaque `Text` nouvellement affichés dans un component [`TouchableOpacity`](https://facebook.github.io/react-native/docs/touchableopacity.html) de React Native (équivalent React Native d'un bouton).**  

**4.4 Modifiez la fonction `onPress` de `TouchableOpacity` afin qu'un tap change la valeur de `strokeWidth` pour la valeur du bouton selectionné.**  
la valeur affichée de `strokeWidth` doit prendre la valeur du `TouchableOpacity` sur lequel vous avez tap.

**4.5 Modifiez la valeur de la props `strokeWidth` de `rn-draw` afin qu'elle soit égale à la valeur de la `strokeWidth` du `state`.**

> ✋ À cette étape, appelez-moi pour que je vienne vérifier votre code. Si tout s'est bien passé, vous pouvez maintenant changer la taille de la mine du crayon !

**4.6 Un peu de style: À la place d'afficher la valeur de la `strokeWidth` sur chaque bouton, affichez un cercle de background `#000` qui aura pour width et height `strokeWidth * 2`.**

**4.7 Modifiez le style des `touchableOpacity` afin que la stroke selectionnée apparaisse de couleur `#358EF6`**

 🎉 Bravo, vous pouvez maintenant changer la taille du trait !
![Congrats](https://media3.giphy.com/media/xT1XGD02MRIfS829qw/giphy.gif)

### 5. Annuler et effacer  
Dans cette partie, nous allons créer deux boutons `annuler`(annule le dernier trait) et `effacer`(Efface l'integralité du canvas).

**5.1 Dans la `View` `actionsContainer`, crèez deux `TouchableOpacity` "Undo" et "Delete"  dont le style est la suivant :**

```
button : {
    paddingVertical: 15,
    borderWidth: 1
}
```

**5.2 Associez les fonctions undo et clear de `rn-draw` à leurs boutons respectifs.

 🎉 Vous pouvez maintenant annuler votre dernier trait ou effacer le canvas !
![Congrats](https://media0.giphy.com/media/e4TrOZ3otE7JK/giphy.gif)


> ✋ Si vous êtes arrivés jusqu'ici, c'est que vous avez fini la partie 1, félicitations ! Appelez moi pour que je vienne vérifier votre exercice.


## Partie 2 : Le jeu
Dans cette partie, nous allons implémenter la logique du jeu.
Le fonctionnement est le suivant : 
Un joueur est le dessinateur, les autres sont ceux qui doivent deviner le mot qui est dessiné.  
Un mot est choisi aléatoirement dans une liste et présenté au dessinateur. Quand celui-ci est prêt, il appuie sur le bouton "go" qui lance la partie, ainsi qu'un timer de 60s.  
Pendant ces 60s, si la solution est trouvée, un bouton "mot trouvé" permet au dessinateur d'annoncer que l'on peut passer au dessinateur et mot suivant.  
Si les 60s sont écoulés, le dessinateur a perdu, et on passe au joueur suivant.


### 6. La liste de mots

