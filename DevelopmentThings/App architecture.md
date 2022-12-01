
Instead of creating `presentation`, `domain` and `data` packages in the root package you put them in separate features 

```
feature_feature1
	data
		data_source
		repository
	domain
		models
		repository
		use_case
	presentation
		screen1
			components
```

I could also include a `core.presentation` package to share things throughout the whole project

Repository directly accesses the data source (database, API) and decides from witch source to forward data from
