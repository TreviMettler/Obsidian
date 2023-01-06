#kotlin 

the room persistence library provides an abstraction layer over SQLite to allow robust database access while harnessing the full power of SQLite

maybe outdated![[Drawing 2022-12-07 08.15.18.excalidraw|1000]]

from developer.android![[Drawing 2022-12-07 08.31.48.excalidraw|1000]]
 
## DAO

### Dao.kt
this is the file where you describe how you wanna manipulate the database
```kotlin
interface NoteDao {
	@Query("SELECT * from notes_tbl")  
	fun getNotes(): Flow<List<Note>>
  
	@Query("SELECT * from notes_tbl WHERE id=:id")  
	suspend fun getNoteById(id: Int): Note  
  
	@Insert(onConflict = OnConflictStrategy.REPLACE)  
	suspend fun insertNote(note: Note)  
  
	@Update(onConflict = OnConflictStrategy.REPLACE)  
	suspend fun updateNote(note: Note)  
  
	@Query("DELETE from notes_tbl")  
	suspend fun deleteAll()  
  
	@Delete  
	suspend fun deleteNote(note: Note)
}
```
these functions should not be run on the main thread because it could freeze up the UI thread if it tries to load a large amount of rows