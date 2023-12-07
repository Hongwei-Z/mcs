### Temporary Title: United Learning - A Distributed Machine Learning Intrusion Detection Model for Wireless Sensor Networks
(United, Allied, Synergistic, Integrated, Associated, Networked) Learning

> #### Author: Hongwei Zhang

> #### Abstract:  
> This is a Wireless Sensor Network (WSN) Intrusion Detection model which includes a server and multiple clients (WSN nodes). Each client has a machine learning model trained using sensor data, and in the server, there is a model trained using network traffic data. The clients encrypt and compress the trained local model and send it to the server. The server receives the models, decompresses and decrypts them and saves the local models to the server. Once the WSN simulation starts, the sensors in the nodes will collect new sensing data, these data need to pass the validation of the local models first. The data that passes the validation will be sent to the server and the data that does not pass will be discarded. Once the server receives the sensed data, it will validate the sensor data and the network traffic generated by the transmitted data by aggregated prediction method to give the final validation result. If the data passes the validation, the data is saved, otherwise, the data is discarded.


> #### Files Description:
>> [requirements.txt](requirements.txt):  `pip install -r requirements.txt`     
>> [helper.py](helper.py): Process the dataset, output model metrics, and generate encryption keys.   
>> [server.py](server.py): Receive data from clients, decrypt, decompress, save, and train network traffic model.  
>> [client1.py](client1.py): Train local sensor model, send data to server, encrypt, compress.   
>> [client2.py](client2.py): Same as above.   
>> [client3.py](client3.py): Same as above.  
> 
>> [aggregated_predict.py](aggregated_predict.py): Includes two aggregated model prediction methods, and one model testing method.   
>> [Demo_Aggregated_Prediction.ipynb](Demo_Aggregated_Prediction.ipynb): A demonstration of the methods in the above file.   
> 
>> [Preprocessing.ipynb](datasets/Preprocessing.ipynb): A demonstration of the dataset preprocessing process.  
>> [merged_data.csv](datasets/merged_data.csv): The new dataset generated by the above file.   



> #### Get Started:
>> 1. Start the server and clients, train the models, transfer the models, and save the models. Open two terminals, one for the server and another for the clients.   
>>      1. In the first terminal, load the helper and start the server:   
>>          ```bash   
>>          python helper.py
>>          python server.py
>>          ```   
>>    
>>      2. In the second terminal, run each of the three clients:   
>>          ```bash
>>          # Note: Run the next client only after seeing the previous client's task completed in the server terminal.
>>          python client1.py
>>          python client2.py
>>          python client3.py
>>          ```
>
>> 2. Test the models using the model aggregated prediction methods in file `aggregated_predict.py`. Run file `Demo_Aggregated_Prediction.ipynb`. This step should be integrated into the server in the WSN simulation,  it is separated here for ease of demonstration.    



> #### Results:
>> 1. Server running results (first terminal):
>>   ```bash
>>    C:\Users>python helper.py
>>    C:\Users>python server.py
>>    Server is waiting for connections ...
>>    --------------------------------------------------------------------------------------------------------------
>>    Connected to Client 1:
>>    Address: ('127.0.0.1', 63042)
>>    
>>    Client 1 model decryption information:
>>    Key: b'6UtywGHbi8npnxPyY4P83P5XcQDHxJuq_lwzaIVxIPc='
>>    Seed: 0.09432617
>>    Salt: b'g\x84P\xa2^#8\x1b\xc0\xca\xdf\xad\x0bn%\xec'
>>    
>>    Receiving Client 1 model file: 100%|███████████████████████████████████████| 236M/236M [05:15<00:00, 786kB/s]
>>    Client 1 model file has been received, time spent: 315.0624 seconds
>>    Client 1 model file size: 236.1866 MB
>>    Client 1 model file has been decompressed and decrypted, time spent: 1.9954 seconds
>>    Client 1 model file has been saved to: ./received_models/client_1.joblib
>>    --------------------------------------------- Client 1 Completed ---------------------------------------------
>>    Connected to Client 2:
>>    Address: ('127.0.0.1', 63056)
>>    
>>    Client 2 model decryption information:
>>    Key: b'1newWib-Z_CJtKuNV5Fylr5kQYADwFF8nm-LPthaYL0='
>>    Seed: 0.09403347
>>    Salt: b'\x05\xa7\x9f\xab)\x96\xaeH|\xf1Z\xdd\xe2\x01\x9e\x1f'
>>    
>>    Receiving Client 2 model file: 100%|███████████████████████████████████████| 234M/234M [05:09<00:00, 792kB/s]
>>    Client 2 model file has been received, time spent: 309.3826 seconds
>>    Client 2 model file size: 233.6859 MB
>>    Client 2 model file has been decompressed and decrypted, time spent: 1.9909 seconds
>>    Client 2 model file has been saved to: ./received_models/client_2.joblib
>>    --------------------------------------------- Client 2 Completed ---------------------------------------------
>>    Connected to Client 3:
>>    Address: ('127.0.0.1', 63090)
>>    
>>    Client 3 model decryption information:
>>    Key: b'mSjV2eLxMvjrdPHDltRFuApMskXJB6WXRSSE4IIm1l0='
>>    Seed: 0.09415671
>>    Salt: b'\xb2\xb3U\x84&\xb8 /[\xa4\x1b$\xc1\xff\x17R'
>>    
>>    Receiving Client 3 model file: 100%|███████████████████████████████████████| 234M/234M [05:08<00:00, 795kB/s]
>>    Client 3 model file has been received, time spent: 308.8740 seconds
>>    Client 3 model file size: 234.2104 MB
>>    Client 3 model file has been decompressed and decrypted, time spent: 1.9963 seconds
>>    Client 3 model file has been saved to: ./received_models/client_3.joblib
>>    --------------------------------------------- Client 3 Completed ---------------------------------------------
>>    --------------------------------------- All Clients Have Been Processed --------------------------------------
>>    Training the global model using network traffic data ...
>>    Label distribution in the training set: {0: 201341, 1: 1940759}
>>   
>>    Global model training completed in 166.3271 seconds.
>>    Global model saved to: ./received_models/global_model.joblib
>>    -------------------------------------------------- All Done --------------------------------------------------
>>    C:\Users>
>>   ```
>
>> 2. Clients running results (second terminal):
>>    ```bash
>>    C:\Users>python client1.py
>>    Client 1:
>>   
>>    Label distribution in the training set: {0: 67352, 1: 646681}
>>    
>>    Client 1 model training completed in 66.3018 seconds.
>>    Client 1 model saved to: ./client_models/client_1.joblib
>>    
>>    Client 1 model encryption information:
>>    Key: b'6UtywGHbi8npnxPyY4P83P5XcQDHxJuq_lwzaIVxIPc='
>>    Seed: 0.09432617
>>    Salt: b'g\x84P\xa2^#8\x1b\xc0\xca\xdf\xad\x0bn%\xec'
>>    
>>    Model file size: 233.8386 MB
>>    Model file encrypted, file size: 311.7849 MB, time spent: 1.3153 seconds
>>    Model file compressed, file size: 236.1866 MB, time spent: 8.6439 seconds
>>    
>>    Client 1 has connected to the server
>>    Model file has been sent from Client 1, file size: 236.1866 MB, time spent: 0.0368 seconds
>>    ----------------------------------- Client 1 Completed -----------------------------------
>>    
>>    C:\Users>python client2.py
>>    Client 2:
>>    
>>    Label distribution in the training set: {0: 67143, 1: 646890}
>>    
>>    Client 2 model training completed in 65.8010 seconds.
>>    Client 2 model saved to: ./client_models/client_2.joblib
>>    
>>    Client 2 model encryption information:
>>    Key: b'1newWib-Z_CJtKuNV5Fylr5kQYADwFF8nm-LPthaYL0='
>>    Seed: 0.09403347
>>    Salt: b'\x05\xa7\x9f\xab)\x96\xaeH|\xf1Z\xdd\xe2\x01\x9e\x1f'
>>    
>>    Model file size: 231.3624 MB
>>    Model file encrypted, file size: 308.4833 MB, time spent: 1.2568 seconds
>>    Model file compressed, file size: 233.6859 MB, time spent: 8.4879 seconds
>>    
>>    Client 2 has connected to the server
>>    Model file has been sent from Client 2, file size: 233.6859 MB, time spent: 0.0360 seconds
>>    ----------------------------------- Client 2 Completed -----------------------------------
>>    
>>    C:\Users>python client3.py
>>    Client 3:
>>    
>>    Label distribution in the training set: {0: 67231, 1: 646802}
>>    
>>    Client 3 model training completed in 86.3497 seconds.
>>    Client 3 model saved to: ./client_models/client_3.joblib
>>    
>>    Client 3 model encryption information:
>>    Key: b'mSjV2eLxMvjrdPHDltRFuApMskXJB6WXRSSE4IIm1l0='
>>    Seed: 0.09415671
>>    Salt: b'\xb2\xb3U\x84&\xb8 /[\xa4\x1b$\xc1\xff\x17R'
>>    
>>    Model file size: 231.8829 MB
>>    Model file encrypted, file size: 309.1773 MB, time spent: 1.7127 seconds
>>    Model file compressed, file size: 234.2104 MB, time spent: 11.1032 seconds
>>    
>>    Client 3 has connected to the server
>>    Model file has been sent from Client 3, file size: 234.2104 MB, time spent: 0.0410 seconds
>>    ----------------------------------- Client 3 Completed -----------------------------------
>>    C:\Users>
>>    ```
>
>> 3. Models aggregated prediction results:   
>> See `Demo_Aggregated_Prediction.ipynb`, section 2.



> #### Citations:   
>> 1. [The TON_IoT Datasets](https://research.unsw.edu.au/projects/toniot-datasets)
>> 2. [scikit-learn: RandomForestClassifier](https://scikit-learn.org/stable/modules/generated/sklearn.ensemble.RandomForestClassifier.html)
>> 3. [Real Python: Socket Programming in Python](https://realpython.com/python-sockets/)
>> 4. [Stack Overflow: Send big file over socket](https://stackoverflow.com/questions/56194446/send-big-file-over-socket)
>> 5. [Cryptography: Fernet](https://cryptography.io/en/latest/fernet/)