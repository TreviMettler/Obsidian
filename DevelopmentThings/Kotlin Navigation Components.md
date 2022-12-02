#kotlin

Navigation component is a set of 3 main parts consisting of:
	Navigation Graph
	NavHost
	NavController

![[navigationCompoentFigure1]]

## Destinations
The screen itself is just a composable the is listed in the `navGraph` 


## Navigation.kt
The main file that enables navigation is where the `navController` is instantiated as well where the `navGraph` is defined
```kotlin
val navController = rememberNavController()  
NavHost(navController = navController,  
    startDestination = HomeScreen.name  
) {  
    composable(HomeScreen.name) {  
        HomeScreen(navController)  
    }  
    composable(DetailsScreen.name) {  
        DetailsScreen(navController = navController)  
    }  
}
```
This is also where you define what the starting screen is