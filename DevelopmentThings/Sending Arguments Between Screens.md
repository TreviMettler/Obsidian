#kotlin #compose #navigation  

## Poping the backstack while passing arguments

This is how to close a screen while also passing arguments
```kotlin
	navController.navigate(Screen.Home.route) {
		popUpTo(Screen.Home.route) {
			inclusive = true
		}
	}
```

## Screens.kt but more..
```kotlin
sealed class Screens(val route: String) {
	object Home: Screen(route = "home_screen")
	object Detail: Screen(route = "detail_screen/{id}")
}
```

## NavHost
```kotlin
val navController = rememberNavController() 
NavHost(navController = navController, 
		startDestination = Screen.Home.route 
) { 
		composable(Screen.Home.route) { 
			HomeScreen(navController) 
		}
		
		composable(
		route = Screen.Detail.route,
		arguments = listOf(navArguments(id){
			type = NavType.IntType
		})
		) { 
			DetailsScreen(navController) 
		} 
}
```