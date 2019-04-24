This is the Jmeter load testing script and data for OpenMRS.
We set 30 users accessing the system for 5 hours (30min warmup, 4hour running, 30min cool down). 

1. Set Web Server IP and Port Number in HTTP Request Defaults, please replace the proper parameters according to your testing environment.

2. Setup user login from HTTP Authorization Manager. Please also replace the parameters according to your setup.

3. Read following data from "data" folder:
	Person.csv: Person UUID. Variable name: ${PERSON}. 
	shuffledPerson.csv: Person UUID after shuffling. Variable name: ${S_PERSON}. 
	PersonName.csv: Person name. Variable name ${PERSON_NAME}.
	ConceptName.csv: Read medical concepts dictionary. Variable name: ${CONCEPT_NAME}.

   These data can be accessed from database.

4. HTTP requests. We pre-define the HTTP header "Content-Type" is "application/json", and some of the HTTP requests contains a JSON request.

	4.1 Add a new person and extract the person's UUID. 

	4.2 Delete this newly added person accoding to his/her UUID.

	4.3 Random number of loops:
		Search a person by his/her name.

	4.4 Random number of loops (>= 1):
		Search a person by his/her UUID.

	4.5 Randomly choose one of the following requests:
		Get encounter from person's UUID (shuffled).
		Get observation from person's UUID (shuffled).
		Return a list of concepts.
		Get concept by concept name.
		Edit a person's information. 

This iteration will be repeated until total running time exceeds 5 hours.


