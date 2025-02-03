## Bleeding Out Methodology: How we calculated stark disparities in trauma care

By <em>Ari Sen & Lauren Caruba</em> 

Tens of thousands of Americans bleed to death every year with injuries they could have survived, researchers say. Traumatic injuries from car crashes, shootings, stabbings, falls and other accidents are the leading killer of children and adults under age 45, and bleeding out is the leading cause of preventable trauma deaths. 

As part of our reporting on these deaths, we examined how geographic disparities impacted outcomes. We hypothesized that patients who are farther from Level I or II trauma centers — which are equipped to treat the most critically injured patients — would have a greater chance of dying before reaching a hospital because of longer transport times. 

Our analysis was informed by academic articles that examined preventable trauma deaths and access to trauma care. We tested our theory at the state, county and U.S. Census Block level, with input from University of Alabama at Birmingham assistant professor and trauma surgeon Dr. Zain Hashmi and his research assistant, medical student Mckinley Williams. We used 2021-22 data from the American Trauma Society, Centers for Disease Control and Prevention and Census Bureau to conduct our analysis. The American Trauma Society, which tracks the location and level of care provided at trauma centers across the country, shared the data under a licensing agreement. 

Data analysis was conducted by Ari Sen. The project was supported by a National Fellowship grant from the University of Southern California’s Center for Health Journalism. 

The findings echo the work of researchers who have linked rural areas with higher mortality rates for injured patients and underscore the need for improved care for these patients.

#### Trauma center data
Trauma centers are categorized according to their level of care on a scale of I to V. Level I provides the highest level of care for injured patients. 

Trauma centers can be designated by either the American College of Surgeons, or ACS, the state or both. Level I trauma centers must have a certain number of surgeons, ER doctors, anesthesiologists, nurses, respiratory therapists and other personnel available 24 hours a day to maintain their designation. Level II trauma centers can treat all levels of injured patients but typically do not have the research capabilities of a Level I center. 

We chose to focus on ACS or state-designated Level I and II centers, as our reporting focuses on major bleeding and they provide the best chance of survival for the most severely injured patients. We did not include hospitals that had only a pediatric Level I or II designation. 

Once our data was filtered, we geocoded all of the addresses to obtain the latitude and longitude for each trauma center.

#### The distance map

We built the map to give readers a clear sense of the geographic disparities in trauma care access between urban centers and rural areas, and to allow readers to test addresses, including their own, to see how far they are from a Level I or II center.

To gauge the distance to each trauma center, we converted our geocoded trauma center data into a spatial file. We changed the coordinate reference system (ie. the framework used to locate points on the Earth’s surface) to compute the distance in meters and subsequently transformed it into miles. 

We obtained the shapefiles for every 2022 Census Block and combined them. We used Blocks because they are the smallest unit of measurement the Census Bureau offers that provides the most accurate distance calculation for the map without geocoding every address in the United States. As with the trauma centers, we converted the block file’s coordinate reference system to compute the distance to our trauma centers in miles. We used Geopandas sjoin_nearest function and the centermost point for each block to calculate the approximate distance to the nearest trauma center. 

Following a tutorial from Texas Christian University professor Kyle Walker, we used the routingpy library and Mapbox’s API to generate drive times to a hospital, called isochrones. We drew the isochrones in 3-minute increments and removed the next smallest area from the center (as if creating a doughnut), until we reached 30 minutes, to avoid overlapping segments. We chose to stop there because studies have indicated trauma mortality increases every minute, especially around the 30-minute mark. 

We developed an algorithm with help from GIS Stack Exchange user BERA to find areas close to multiple trauma centers, because some locations are close to multiple hospitals. It starts by extracting the boundaries; combines them into a multiline shape by merging the overlapping segments; builds new shapes; and associates them with the corresponding information from the original polygons.

For areas beyond 30 minutes, we estimate travel time using the distance from the center of census blocks to the nearest trauma center with an average speed of 45 mph.

Our map gives readers an understanding of their proximity to high-level trauma care. It also accounts for geographic features common in states like Colorado that impact accessibility, such as rough terrain, lack of paved roads or bodies of water.  The map also shows how well dense metropolitan areas like Dallas-Fort Worth are served by Level I and II trauma centers. 

#### Conclusion
Our interviews and the medical literature suggested distance and time to high-quality trauma care play a major role in outcomes after a major injury.

Our map allows readers to see these disparities, including the country’s expansive trauma care deserts, and shows how they apply to their own communities. 















