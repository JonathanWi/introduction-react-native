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

![Congrats](https://media0.giphy.com/media/XreQmk7ETCak0/giphy.gif)


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

**5.2 Associez les fonctions undo et clear de `rn-draw` à leurs boutons respectifs.**

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

Téléchargez le fichier words.js présent dans ce repo, (il contient une longue liste de mots pour le jeu) et placez ce fichier à la racine de votre dossier (au même niveau que `App.js`).

**6.1 Importez la liste de mot dans le fichier `App.js` dans une variable `words`**

**6.2 Dans le `constructor`, initialisez le state `words` qui a pour valeur la liste de mot mélangée aleatoirement.**

**6.3 Dans le `constructor`, initialisez le state `currentWordIndex` à la valeur `0`. Cette variable correspond à l'index du mot en cours dans le tableau `this.state.words`**

**6.4 Affichez le mot en cours dans la `View` `actionsContainer`**

**6.5 Passer au mot suivant : créez un bouton mot trouvé (grâce à `TouchableOpacity`). Un tap sur ce bouton déclenche le passage au mot suivant**

> ✋ Si vous êtes arrivés jusqu'ici, appelez moi pour que je vérifie votre exercice : si tout fonctionne vous devriez voir le mot changer à chaque tap.

### 7. La logique du jeu
Dans cette partie nous allons implémenter la logique générale du jeu. Il existe trois états distincts :

- `wordFound` : le mot a été trouvé, on affiche un écran de félicitations, et un bouton pour passer au mot suivant.
- `wordFail` : le mot n'a pas été trouvé, on affiche un message de défaite, et un bouton pour passer au mot suivant.
- `gameStarted`: tant que la partie n'a pas commencée, on affiche le mot a dessiner pour le dessinateur.

Le mot a dessiner ainsi que le message de succès (et de défaite) sont présentés dans une modal ([react-native-simple-modal](https://github.com/bodyflex/react-native-simple-modal)).

**7.1 Initialisez 3 variables du state `wordFound`, `wordFail` et `gameStarted` avec pour valeur `false`.**

**7.2 Installez et importez [`react-native-simple-modal`](https://github.com/bodyflex/react-native-simple-modal) dans le fichier `App.js`.**

**7.3 Ajoutez la modal dans le render de `App` et ajoutez les bonnes conditions pour lesquelles la props `open` de la modal est à `true`.**

**7.4 Dans la modale, si la partie n'a pas démarrée, affichez le mot à dessiner, ainsi qu'un bouton qui démarre la partie**

**7.5 Dans la modale, si la partie a démarrée et que le mot a été trouvé, affichez un message de succès et un bouton pour passer au mot suivant**

**7.6 Dans la modale, si la partie a démarrée et que le mot n'a pas été trouvé, affichez un message d'échec et un bouton pour passer au mot suivant.**

**7.7 Dans le `View` `actionsContainer`, ajoutez un bouton "mot trouvé" qui finit la partie au tap.**

> ✋ Si vous êtes arrivés jusqu'ici, appelez moi pour que je vérifie votre exercice : si tout fonctionne vous devriez voir le mot à dessiner dans une modal, puis le jeu. Au tap sur le bouton "mot trouvé", je vois un message de succès dans la modal accompagné d'un bouton "mot suivant". Au tap sur ce bouton, le processus décrit recommence.

### 8. Le timer

Dans cette partie, nous allons installer un compte à rebours. Lorsque celui-ci est fini la partie est terminée et le mot n'a pas été trouvé.

**8.1 Installez et importez [`react-native-countdown-circle`](https://github.com/MrToph/react-native-countdown-circle) dans le fichier `App.js`**


**8.2 Créez une fonction `this._onWordFail` dans le component `App`. Quand elle est appelée, cette fonction retourne `console.log('fail')`.**

**8.2 Ajoutez le Countdown dans la `View` `DrawContainer` et positionnez le en absolute. Le code du countdown est le suivant :**

```jsx
<CountdownCircle
    seconds={60}
    radius={25}
    borderWidth={4}
    color="#F05E9F"
    bgColor="#fff"
    onTimeElapsed={this._onWordFail}
    />
```
⚠️ Ne pas copier l'exemple sur le site de `react-native-countdown-circle`, uniquement le code ci-dessus !


**8.3 Ajoutez une condition afin que le countDown n'apparaisse que lorsque la partie a commencée.**


**8.4 Faites en sorte que la fonction `_onWordFail` soit appelée quand le `countDown`est terminé. La modale d'échec doit alors s'afficher !**


![Congrats](https://media0.giphy.com/media/lD76yTC5zxZPG/giphy.gif)

