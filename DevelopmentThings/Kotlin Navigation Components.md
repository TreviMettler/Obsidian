#kotlin

Navigation component is a set of 3 main parts consistinf of:
	Navigation Graph
	NavHost
	NavController

### Navigation Component 
	NavController - the central API that instructs navigation to occur  `navigate.navigation(route)`
		NavHost - Hosts each navigation graph item and swaps destinations(composables) when requested
				NavGraph - Holds infomation about destinations/composables and maps them 

### NavGraph
	Composables
		