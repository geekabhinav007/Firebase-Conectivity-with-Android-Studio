# What is Firebase?

Firebase is a backend platform for building web, Android and iOS applications. It offers real-time database, authentication services, storage solutions, and various other tools and services to help developers build high-quality apps faster. Firebase is developed by Google and is available as a cloud service, with support for multiple programming languages.

## what we use Firebase?

There are several reasons why developers choose to use Firebase:

- Real-time database: Firebase's real-time database enables real-time synchronization of data across all connected devices.

- Easy authentication: Firebase provides easy-to-use authentication services for email/password, phone number, and other popular identity providers.

- Scalability: Firebase is built to scale automatically and can handle large amounts of traffic and data.

- Hosting: Firebase also provides hosting services for web applications, making it easy to deploy and serve web content.

- Integration: Firebase integrates with other Google services and other popular tools, making it a comprehensive platform for developing, deploying, and managing applications.

- Affordable: Firebase provides many services for free or at a very affordable cost, making it a cost-effective solution for small and large scale applications.

## what are the alternatives of firebase?

Some alternatives to Firebase include:

- AWS (Amazon Web Services): A cloud computing platform that offers a variety of services including databases, storage, and authentication.

- Heroku: A cloud platform for deploying, managing, and scaling web applications.

- Parse: A Backend-as-a-Service platform that provides a complete backend for mobile and web applications.

- MongoDB Atlas: A fully managed cloud database service for modern applications.

- Microsoft Azure: A cloud computing platform that offers a variety of services including databases, storage, and authentication.

- Back4App: A Backend-as-a-Service platform that provides a complete backend for mobile and web applications built with Parse technology.

- PostgreSQL: A free and open-source relational database management system.

- Realm: An open-source mobile database platform designed for mobile devices.

## Some essential code to add to connect to firebase from anroid studio

To connect your Android app to Firebase, you can follow these steps:

- Create a Firebase project in the Firebase console.

- Go to the Firebase console and click on the Android icon to register your app.

- Enter your app's package name and provide a default nickname for your app.

- Download the "google-services.json" file from the Firebase console and place it in the "app" directory of your Android Studio project.

- Add the following lines to your project-level build.gradle file:

```javascript
buildscript {

    dependencies {
        // Add the dependency for the Google services Gradle plugin
        classpath 'com.google.gms:google-services:4.3.15'
    }
}
```

- Add the following lines to your app-level build.gradle file:

```javascript

plugins {
    //below is alredy there
    id 'com.android.application'
    // this to be added
    // Add the Google services Gradle plugin
    id 'com.google.gms.google-services'

}
```

```javascript
dependencies{

    implementation 'com.google.firebase:firebase-database:20.0.4'

}
```

- Sync your gradle files by clicking on "Sync Now" in the top right corner of the Android Studio window.

- Initialize Firebase in your app's main activity:

`M-1`

```java
import com.google.firebase.FirebaseApp;

public class MainActivity extends AppCompatActivity {

  @Override
  protected void onCreate(Bundle savedInstanceState) {
    super.onCreate(savedInstanceState);
    setContentView(R.layout.activity_main);

    // Initialize Firebase
    FirebaseApp.initializeApp(this);
  }
}
```

`M-2`

The code `FirebaseFirestore firestore`; declares a variable `firestore` of type `FirebaseFirestore`. It is used to interact with the Firebase Firestore database.

The Firebase Firestore library is a NoSQL document-based database provided by Firebase. It allows you to store and retrieve data in real-time, as well as perform complex queries and transactions on the data.

The `firestore` variable can be used to perform various operations such as reading data from the database, writing data to the database, updating data, and deleting data.

```java
   FirebaseFirestore firestore;
```

The code `import com.google.firebase.firestore`.FirebaseFirestore; is an import statement in Java. It is used to include the `FirebaseFirestore` class from the `com.google.firebase.firestore` package into the current Java file.

```java
import com.google.firebase.firestore.FirebaseFirestore;
```

```java
import  java.util.Map;
```

below code is used to store data in the Firebase Firestore database.

- `firestore = FirebaseFirestore.getInstance();`: This line creates an instance of the `FirebaseFirestore` class and assigns it to the `firestore` variable. The `FirebaseFirestore.getInstance()` method returns a singleton instance of the `FirebaseFirestore` class, which can be used to interact with the Firebase Firestore database.

- `Map<String, Object> users = new HashMap<>();`: This line declares a variable `users` of type `Map<String, Object>`, which is a collection of key-value pairs. The keys are strings and the values are objects. This map will be used to store data that will be added to the Firebase Firestore database.

- `users.put("firstName", "Kumar");`: This line adds a key-value pair to the `users` map, where the key is "firstName" and the value is "Kumar".

- `firestore.collection("users").add(users)`: This line adds the data stored in the `users` map to a collection named "users" in the Firebase Firestore database. The `add` method returns a `Task` object that represents the asynchronous operation of adding data to the database.

- `.addOnSuccessListener(new OnSuccessListener<DocumentReference>() { ... })`: This line registers a success listener for the `Task` returned by the `add` method. The success listener is an instance of the `OnSuccessListener<DocumentReference>` interface, and it takes a `DocumentReference` object as an argument. If the add operation is successful, the `onSuccess` method is called and a toast message "Success" is displayed.

- `.addOnFailureListener(new OnFailureListener() { ... })`: This line registers a failure listener for the `Task` returned by the `add` method. The failure listener is an instance of the `OnFailureListener` interface, and it takes a `Exception` object as an argument. If the add operation fails, the `onFailure` method is called and a toast message "Failure" is displayed.

```java

        // Code For Firebase Data Storage

        firestore = FirebaseFirestore.getInstance();
        Map<String, Object> users = new HashMap<>();
        users.put("firstName", "Kumar");
        users.put("lastName", "Abhinav");
        users.put("year", "3rd Year IT");

        users.put("firstName2","H.S");
        users.put("lastName2","Rai");
        users.put("post", "HOD CIVIL");

        firestore.collection("users").add(users).addOnSuccessListener(new OnSuccessListener<DocumentReference>() {
            @Override
            public void onSuccess(DocumentReference documentReference) {
                Toast.makeText(getApplicationContext(), "Success", Toast.LENGTH_LONG).show();
            }
        }).addOnFailureListener(new OnFailureListener() {
            @Override
            public void onFailure(@NonNull Exception e) {
                Toast.makeText(getApplicationContext(), "Failure", Toast.LENGTH_LONG).show();
            }
        });
```
