# Sensor_to_InfluxDB

Questo progetto consiste nel aver creato degli script in python per trasferire dati che arrivano da sensori o altri database dentro il database influxDB.
Ci sono 6 file contenuti in due cartelle chiamate field e tag.
Queste due cartelle a loro volta contengo 3 cartelle contenenti :

	-storicometeociclo: dato una cartella contenente file nominati meteoptf1.txt,meteoptf2.txt,etc... in maniera consecutiva consente di inserirli nel database automaticamente avviando lo script passdatameteociclo.py 

	-streammeteo: consente di fare una richiesta al sensore meteo per ottenere le rilevazioni in tempo reale. Nel caso il file fosse già stato inserito nel database viene ignorato. Si avvia eseguendo lo script real_time_meteo.py (accetta rilevazioni una alla volta)

	-streamwap: Dato un file export.wap contenente le rilevazioni delle onde e i file da 1 a 15 export.cXX (dove XX è il valore positivo della profondita) delle rilevazioni alle varie profondità lo inserisce automaticamente nel database. Nel caso i dati siano già stati inseriti non fa nulla. E' pensato per essere utilizzato con una richiesta diretta al sensore della rilevazione come il precedente streammeteo.

La differenza tra le due cartelle è il modo con cui i dati vengono inseriti:
	
	-tag: 
		measurement,<tag vari>,observed_property=<property1 name> value=<value1>
		measurement,<tag vari>,observed_property=<property2 name> value=<value2>...

	-field: 
		measurement,<tag vari> <property1 name>=<value1>,<property2 name>=<value2>...
