# A Sample Exercise with Apache Nifi on AWS EC2 Server
<p> <br/ >
 
### 1- Login to AWS and launch an instance
<img width="1234" alt="Ekran Resmi 2022-02-27 20 40 21" src="https://user-images.githubusercontent.com/91700155/155900685-8e6362b9-c33b-46e3-aa73-eb1f055f87f8.png">

### 2- Select Ubuntu Server 20.04 LTS
<img width="1407" alt="Ekran Resmi 2022-03-12 16 46 19" src="https://user-images.githubusercontent.com/91700155/158027433-fa577f0c-66b9-4c8e-9655-3695215a9663.png">

### 3- Choose an Instance Type (Choose recommended)
<img width="1421" alt="Ekran Resmi 2022-03-12 16 48 04" src="https://user-images.githubusercontent.com/91700155/158027459-3af8239b-8aa7-499f-9e84-94071ca5cb4c.png">

### 4- Size installations we can add additional volume
<img width="1421" alt="Ekran Resmi 2022-03-12 16 48 04" src="https://user-images.githubusercontent.com/91700155/158027486-89a91372-2f35-448c-9850-ccc3171fa95e.png">

### 5- Make sure the security group type has all traffic allowed to inbound and outbound that you need
<img width="1421" alt="Ekran Resmi 2022-03-12 16 49 43" src="https://user-images.githubusercontent.com/91700155/158027508-ceac9ad2-9df1-43d8-a895-e4482cf89426.png">

### 6- Create a Private Key file (.pem)
<img width="1422" alt="Ekran Resmi 2022-03-12 16 50 39" src="https://user-images.githubusercontent.com/91700155/158027515-5356d3fe-016e-4ef8-9318-92ec470186ce.png">

### 7- Launch the Instance
<img width="1422" alt="Ekran Resmi 2022-03-12 16 50 56" src="https://user-images.githubusercontent.com/91700155/158027558-36439ca4-dd08-404a-90c6-75d3c7c9f51f.png">
<img width="1434" alt="Ekran Resmi 2022-03-12 16 54 42" src="https://user-images.githubusercontent.com/91700155/158027574-089e3ad0-b9bf-4d4e-94f4-2a875d33ddeb.png">

### 8- Change the permission of Private Key
```console
chmod 400 <pem file name>.pem
```
### 10- Connect using SSH
```console
ssh -i <pem file name> ubuntu@public-dns-name
```
<img width="878" alt="Ekran Resmi 2022-03-12 16 55 09" src="https://user-images.githubusercontent.com/91700155/158027635-3cb2a7c6-0e2e-407d-b537-a4b2de324c4c.png">

### 11- Installing Java 
```console
sudo apt update
sudo apt upgrade
sudo apt install openjdk-11-jdk
```
### 12- Installing Apache Nifi from the web site https://archive.apache.org/dist/nifi/1.13.2/
```console
wget https://archive.apache.org/dist/nifi/1.13.2/nifi-1.13.2-bin.tar.gz
```
#### Extract the saved archive using tar
```console
tar -xvf nifi-1.13.2-bin.tar.gz
```
<img width="887" alt="Ekran Resmi 2022-03-12 16 58 33" src="https://user-images.githubusercontent.com/91700155/158027886-b68b61b4-2aa6-450a-b00e-77ef3a8529a0.png">
  
#### Show the file and configure the properties
```console
cd nifi-1.13.2/
nano conf/nifi.properties
```
<img width="887" alt="Ekran Resmi 2022-03-12 16 59 40" src="https://user-images.githubusercontent.com/91700155/158028006-bac4edd9-a704-4838-bdb6-1a47bda35a32.png">

#### Delete the "nifi.web.http.host" value
```console
cd nifi-1.13.2/
nano conf/nifi.properties
```
<img width="885" alt="Ekran Resmi 2022-03-12 17 01 06" src="https://user-images.githubusercontent.com/91700155/158028044-83bd549c-9ea7-4836-b714-8159c9f0f3ee.png">
 
### Start Server
```console
bin/nifi.sh start
bin/nifi.sh status
```
<img width="874" alt="Ekran Resmi 2022-03-12 17 06 46" src="https://user-images.githubusercontent.com/91700155/158028133-38226dca-bad7-4e3a-bb96-1d03e2157c1a.png">

#### Nifi Web UI
```console
http://<yourpublicdns>:8080/
```
<img width="1436" alt="Ekran Resmi 2022-03-12 17 07 48" src="https://user-images.githubusercontent.com/91700155/158028245-49684cfb-115c-4da7-818b-2e056622d9b3.png">
  
<p>  <br />
</p>
  
## Create a sample on Nifi : Http File Transformation
### 1- Create a file for simple examples 
```console
mkdir odev
```
<img width="356" alt="Ekran Resmi 2022-03-12 19 44 20 kopyası" src="https://user-images.githubusercontent.com/91700155/158028201-d43409e5-e8c8-4ced-bcc1-7c5ebe0ab8ef.png">


### 2- Get the file from HTTP endpoint (which we used in the Nifi lecture) 
#### Select a processor from the tab  
<img width="521" alt="Ekran Resmi 2022-03-12 19 03 23" src="https://user-images.githubusercontent.com/91700155/158028446-39681dc5-79f1-4366-a344-8a194b8242f6.png">
  
#### Choose the "InvokeHTTP" from the Processor Panel
<img width="796" alt="Ekran Resmi 2022-03-12 19 09 13" src="https://user-images.githubusercontent.com/91700155/158028617-dc1eecd3-f838-4b3e-bef8-eadfb4334cad.png">
<img width="925" alt="Ekran Resmi 2022-03-12 19 04 34" src="https://user-images.githubusercontent.com/91700155/158028619-8a277a86-8788-4fe5-8cc3-f7fe5be59232.png">
 
##### Configure processor
<img width="789" alt="Ekran Resmi 2022-03-12 19 08 11" src="https://user-images.githubusercontent.com/91700155/158028740-7ec0fe64-7a88-41a4-bcc8-173caa782340.png">
<img width="789" alt="Ekran Resmi 2022-03-12 19 08 03" src="https://user-images.githubusercontent.com/91700155/158028749-71eaf25d-6bb0-4cee-ac8c-7ae1ab422460.png">

##### Sample json file : "https://geoserver.nottinghamcity.gov.uk/opendata/geojson/ncc_Recycling_Centres.json"  
<img width="789" alt="Ekran Resmi 2022-03-12 19 07 16" src="https://user-images.githubusercontent.com/91700155/158028759-13760653-bd51-496f-8c97-729fa2083c15.png">

#### Choose the "UpdateAttribute" from the Processor Panel
<img width="698" alt="Ekran Resmi 2022-03-12 19 16 53" src="https://user-images.githubusercontent.com/91700155/158029064-d077001a-47da-49d4-86ea-bb5e9a8f3dca.png">
 
#### Connect between the "InvokeHTTP" and "UpdateAttribute"
<img width="698" alt="Ekran Resmi 2022-03-12 19 16 53" src="https://user-images.githubusercontent.com/91700155/158029188-c80fca24-5eca-4de7-be26-0f719d2c00a0.png">
<img width="764" alt="Ekran Resmi 2022-03-12 19 19 08" src="https://user-images.githubusercontent.com/91700155/158029448-047fcb00-05c5-474c-a5b1-df7cc740bc2f.png">
<img width="347" alt="Ekran Resmi 2022-03-12 19 19 27" src="https://user-images.githubusercontent.com/91700155/158029220-383585de-1d4f-4425-bcfa-99f3e99cfcf6.png">

### 3- Convert Json file to CSV file using ConvertRecord Processor
#### Choose the "ConvertRecord" from the Processor Panel
<img width="803" alt="Ekran Resmi 2022-03-12 19 19 54" src="https://user-images.githubusercontent.com/91700155/158029304-85834b9c-3e27-4c5b-aef8-39310b8f52df.png">
##### Configure processor
<img width="768" alt="Ekran Resmi 2022-03-12 19 20 19" src="https://user-images.githubusercontent.com/91700155/158029475-6b0ffa0a-3753-4dd0-9410-c8f8d2478efd.png">
<img width="347" alt="Ekran Resmi 2022-03-12 19 20 33" src="https://user-images.githubusercontent.com/91700155/158029486-e59d3c42-32ce-4acf-b73b-2169296e7edb.png">
#### Set your directory
<img width="792" alt="Ekran Resmi 2022-03-12 19 35 38" src="https://user-images.githubusercontent.com/91700155/158030051-c9c043da-f63d-48d6-ad20-7cc5a4d18aaa.png">
##### Add the "Record Reader"
 <img width="833" alt="Ekran Resmi 2022-03-12 19 29 17" src="https://user-images.githubusercontent.com/91700155/158030286-b2c72d92-9642-44be-99ac-2222cfd7f887.png">
##### Add the "Record Writer"
<img width="833" alt="Ekran Resmi 2022-03-12 19 30 20" src="https://user-images.githubusercontent.com/91700155/158030140-a7b4b6d8-da94-41ef-b0d6-63b791bfb0bd.png">
##### Make sure the state is "Enabled"
<img width="1374" alt="Ekran Resmi 2022-03-12 19 31 35" src="https://user-images.githubusercontent.com/91700155/158030203-0f3b6085-b58d-452d-b2be-a14b2717be22.png">
#### For the "ConvertRecord", add "Funnel" section from tab 
<img width="653" alt="Ekran Resmi 2022-03-12 19 34 33" src="https://user-images.githubusercontent.com/91700155/158031044-4e8f8268-3a0e-4dff-825c-c88ac26e3831.png">
<img width="667" alt="Ekran Resmi 2022-03-12 19 34 59 kopyası" src="https://user-images.githubusercontent.com/91700155/158030393-2199d6f2-4436-4eb9-899e-abb86b146223.png">
#### "Failure" button can be selected in the connection 
<img width="760" alt="Ekran Resmi 2022-03-12 19 34 45" src="https://user-images.githubusercontent.com/91700155/158030411-5cd84db5-0316-4073-9970-4f617f9ee18b.png">

  
  
### 4- : Put the flowfile into a directory. (you can use nifi-outputs directory or create a directory for yourself)
#### Choose the "PutFile" from the Processor Panel
<img width="796" alt="Ekran Resmi 2022-03-12 19 21 08" src="https://user-images.githubusercontent.com/91700155/158029560-575f79b6-e446-4021-951a-da70ae207926.png">
#### Configure processor
<img width="790" alt="Ekran Resmi 2022-03-12 19 38 59" src="https://user-images.githubusercontent.com/91700155/158030553-7dabf336-b365-43b4-b4e3-dbacc3949bdf.png">
<img width="792" alt="Ekran Resmi 2022-03-12 19 35 48" src="https://user-images.githubusercontent.com/91700155/158029995-2c3ba0ab-131b-480d-9f7b-e8c15d32e002.png">


#### Connect between the "ConvertRecord" and "PutFile"
<img width="1080" alt="Ekran Resmi 2022-03-12 19 34 59" src="https://user-images.githubusercontent.com/91700155/158030430-9f7fbed9-6eb1-45a9-bf0a-5af20aaec88a.png">
#### "Success" button can be selected in the connection 
<img width="763" alt="Ekran Resmi 2022-03-12 19 25 14" src="https://user-images.githubusercontent.com/91700155/158029631-7dabe9d9-6b68-4557-8df9-569d27ba17e8.png">

#### For the "PutFile", add "Funnel" section from tab 
<img width="706" alt="Ekran Resmi 2022-03-12 19 26 16" src="https://user-images.githubusercontent.com/91700155/158029728-390beb51-7419-4fa4-8511-f6b12830367b.png">
#### Connect between the "PutFile" and "Funnel"
<img width="565" alt="Ekran Resmi 2022-03-12 19 38 15" src="https://user-images.githubusercontent.com/91700155/158030498-57e24dae-9273-4217-8b1d-c3c637676ab0.png">
#### Configure between the "PutFile" and "Funnel". "Success" button can be selected in the connection 
<img width="758" alt="Ekran Resmi 2022-03-12 19 38 30" src="https://user-images.githubusercontent.com/91700155/158030516-a0ee2423-cdd1-4938-819e-2cc215d8f953.png">
### The queue is below: 
<img width="1384" alt="Ekran Resmi 2022-03-12 19 39 15" src="https://user-images.githubusercontent.com/91700155/158030755-a6bb23a8-6f33-40d5-8315-b0b7a83603e1.png">
   

### 5- : Use GetFile processor and read the csv file which you put into a directory.
#### Choose the "GetFile" from the Processor Panel
<img width="798" alt="Ekran Resmi 2022-03-12 19 39 46" src="https://user-images.githubusercontent.com/91700155/158030612-e9e7bb20-7d2d-4fe9-a606-418bee14cf1f.png">
#### Configure processor
<img width="792" alt="Ekran Resmi 2022-03-12 19 41 14" src="https://user-images.githubusercontent.com/91700155/158030804-352d9c82-c520-4947-ab4c-7dc42e657e73.png">
#### Configure between the "PutFile" and "Funnel". "Success" button can be selected in the connection 
<img width="320" alt="Ekran Resmi 2022-03-12 19 40 15" src="https://user-images.githubusercontent.com/91700155/158030622-55562479-54ae-4451-af19-2bb2b69264ac.png">
<img width="798" alt="Ekran Resmi 2022-03-12 19 40 20" src="https://user-images.githubusercontent.com/91700155/158030672-57adb47a-fdc1-4ac7-a6f5-9c2b51c58e6b.png">
<img width="560" alt="Ekran Resmi 2022-03-12 19 44 54" src="https://user-images.githubusercontent.com/91700155/158030659-392995df-3da5-4c24-b52c-9b706dde0b7b.png">
### The last queue is below:   
<img width="1440" alt="Ekran Resmi 2022-03-12 19 43 32" src="https://user-images.githubusercontent.com/91700155/158030818-af25d60a-94b8-426e-b841-4a68054792a5.png">
### Now we can check from the terminal
<img width="885" alt="Ekran Resmi 2022-03-12 19 44 20" src="https://user-images.githubusercontent.com/91700155/158030910-6f9b5f5e-7081-4c65-8d51-e16ef6e1e539.png">


#### And we can see translated files
<img width="491" alt="Ekran Resmi 2022-03-12 19 45 18" src="https://user-images.githubusercontent.com/91700155/158030890-eccde32c-00ec-44e9-a48e-135fadd6cd1f.png">
<img width="1424" alt="Ekran Resmi 2022-03-12 19 45 49" src="https://user-images.githubusercontent.com/91700155/158030902-f902c396-6d9b-4b9d-991b-a9d8ebde6bd4.png">
<img width="1426" alt="Ekran Resmi 2022-03-12 19 45 59" src="https://user-images.githubusercontent.com/91700155/158030919-f254c5ae-e26d-4160-bc8c-e7729d85ebf0.png">

  
#### To stop services
```console
bin/nifi.sh stop
```
<img width="880" alt="Ekran Resmi 2022-03-12 19 47 42" src="https://user-images.githubusercontent.com/91700155/158030971-37572ed3-2272-4fcd-a3ed-a1d19931105e.png">


<p>  <br />
</p>

 ## Seda Atalay
