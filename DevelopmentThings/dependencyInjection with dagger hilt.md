
>hilt is is built on top of dagger to provide a standard way to incorporate dagger

dependency injection helps keep the single responsibility rule
it also allows better testing and easier refactoring

---
### wrong
```kotlin
fun main() {
	val car = Car()
	car.startCar()
}

class Engine() {
	fun start() { println("Engine Started...") }
}

class Car() {
	val engine = Engine()
	fun startCar() { println("Car Started...") }
}
```
### right
```kotlin
fun main() {
	val engine = Engine()
	val car = Car(engine)
	car.startCar()
}

class Engine() {
	fun start() { println("Engine Started...") }
}

class Car(val engine: Engine) {
	fun startCar() { println("Car Started...") }
}
```




---
---

## setting up...

### build.gradle (_projectname_)
```kotlin
buildscipt {
	...
	hilt_version = '2.44.2'
}
dependencies {
	...
	classpath "com.google.dagger:hilt-android-gradle-plugin:$hilt_version"
}
```

### other build.gradle (:app)
```kotlin
plugins {
	...
	id 'kotlin-kapt'
	id 'dagger.hilt.android.plugin'
}

dependencies {
	...
	implemtation "com.google.dagger:hilt-android:$hilt_version"
	kapt "com.google.dagger:hilt-compiler:$hilt_version"
}
```

---

### Application.kt

this creates a application level dependency container allowing hilt to provide dependencies throughout the project
```kotlin
@HiltAndroidApp	
class App: Application() {}
```

>don't forget to add the file to the manifest file

add `@AndroidEntryPoint` to  `MainActiviy` 

---

### AppModule.kt
is where we tell hilt how to create the dependencies
these functions will be used internally so we dont have to do it ourselves0  

```kotlin
@InstallIn(SingletonComponent::class)
@Module
object AppModule {

	@Singleton
	@Provides
	fun provideDao(database: Database): DatabaseDao
	= database.dao()
}
```