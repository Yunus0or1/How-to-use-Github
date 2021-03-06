# Dart 

- Install Dart from this [link](https://www.dartlang.org/tools/sdk)
- Install StageHand

  ```
  pub global activate stagehand [only once. After installation no need to run this command again]
  ```
 - To install Dart project from command line use these commands.
 
   ```
   mkdir fancy_project [create directory]
   cd fancy_project    [browse to directory]
   stagehand package-simple [create Dart project which includes pubspec.yaml and many other files]
   ```
   
# Protocol Buffer

 - Go to this [link](https://github.com/protocolbuffers/protobuf/releases) first to download ProtoC
 - Now create a new folder named **ProtoC** in ***C:/Program Files(x86)*** and extract the downloaded file in ProtoC.
 - You will find three new files. I have downloaded ProtoC v3.7.1 windows x64 file.
 - Now copy the exe path. For my case this is : ***C:/Program Files(x86)/ProtoC/bin***
 - Open up Start and search Environment Variable. Go to Advanced->Environment Variables..
 - In System variable section find PATH, double click it and click on New.
 - Paste the path you copied.
 - Start CMD and write this command :
   ``` 
   protoc --version
   ``` 
   >It should show libprotoc 3.7.1
   
**You have successfully installed Protocol Buffer.**


# Dart with ProtoBuf

 - When installing a Dart project it will not have all the packages. So some commands must be executed in order to use Protocl Buffer
in Dart. First write this command :
   ```
   pub global activate protoc_plugin  [only once to dowload Procol buffer plugin for Dart]
   ```
 - To link all the packages between Dart and Procol Buffer use this command :
   ```
   pub get [This will generate a .pacakages file which contains all local links of Dart libraries]
   ```
 - Go to pubspec.yaml and add this under 'dev_dependencies' add this dependency :
   ```
   protobuf: ^0.10.1
   grpc: ^1.0.2
   ```
 - Now inside the Dart project create a folder named 'protos'. Write a .proto file inside it for example it is 'data.proto' . 
 - To produce ProtoBuf auto generated with gRPC files write this command for Dart :
   ```
   protoc --dart_out=grpc:lib proto/data.proto  [ 'lib' means create auto generated files in directory 'lib']
   ```
   > --dart_out=grpc:lib means you are omitting auto generated proto files with grpc extension and the files will be saved under ***lib/protos*** folder. The protos folder will be generated automatically (at least for my case). You will find four files which have these extensions :
   ```
    <your_proto_file_name>.pb.dart
    <your_proto_file_name>.pbenum.dart
    <your_proto_file_name>.pbgrpc.dart
    <your_proto_file_name>.pbjson.dart
   ```

# Important discussion: Why 'lib' folder is crucial for Dart

When you create a Dart file it will create a lib folder. This is not an ordinary file. The package in Dart includes this file's path. Let's have an example. The Dart project is in a folder named 'Hello' and you can find 'lib' folder under "Hello".So your proto auto generated files are in 'lib/protos'. When you try to access thosed proto files you have to call the path like this.
   ```
   import 'package:Hello/protos/<your_proto_file_name>.pb.dart'
   ```
Importing Package directly calls the 'lib' folder path. So you need not to call this. So basically this is how 'lib' folder is treated.

# Update Proto Dependency
  
  ```
  pub global activate protoc_plugin
  ```
    














