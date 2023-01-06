#kotlin #compose

Navigation component is a set of 3 main parts consisting of:e
	Navigation Graph
	NavHost
	NavController

![[navigationCompoentFigure1]]

## Destinations
The screen itself is just a composable the is listed in the `navGraph` 

---

## Screens.kt
By using sealed classes you can easily keep track of destination
```kotlin
sealed class Screens(val route: String) {
	object Home: Screen(route = "home_screen")
	object Detail: Screen(route = "detail_screen")
}
```



## NavGraph
The main file that enables navigation is where the `navController` is instantiated as well where the `navGraph` is defined
```kotlin
val navController = rememberNavController()  
NavHost(navController = navController,  
    startDestination = Screen.Home.route  
) {  
    composable(Screen.Home.route) {  
        HomeScreen(navController)  
    }  
    composable(Screen.Detail.route) {  
        DetailsScreen(navController)
    }  
}
```
This is also where you define what the starting screen is

## NavController
Keeps track of the back stack and the state of composable screens

## NavHost
Defines the NavGraph and define the start destination

