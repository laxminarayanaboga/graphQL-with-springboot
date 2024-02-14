# Getting Started

### Reference Documentation
For further reference, please consider the following sections:

* [Official Apache Maven documentation](https://maven.apache.org/guides/index.html)
* [Spring Boot Maven Plugin Reference Guide](https://docs.spring.io/spring-boot/docs/2.3.1.RELEASE/maven-plugin/reference/html/)
* [Create an OCI image](https://docs.spring.io/spring-boot/docs/2.3.1.RELEASE/maven-plugin/reference/html/#build-image)


## How to access

* access the graphql service using below url.
    * http://localhost:8080/app-ui

* Use the Altair GraphQL client chrome extension.
    * url: http://localhost:8080/student-service


## Sample queries:
### Query:
```
query {
  student(id: 2) {
    firstName
    lastName
    id
    fullName
    city
    id

    learningSubjects(subjectNameFilter: All) {
      id
      marksObtained
      subjectName
    }
  }
}

```

### Query with variables:
```
query student($id: Long) {
  student(id: $id) {
    id
    firstName
    lastName
    email
    street
    city
    learningSubjects(subjectNameFilter: All) {
      id
      subjectName
      marksObtained
    }
    fullName
  }
}

=================

variables: 

{
  "id": 12
}
```


### mutation: 
```
# Welcome to Altair GraphQL Client.
# You can send your request using CmdOrCtrl + Enter.

# Enter your graphQL query here.

mutation {
  createStudent(
    createStudentRequest: {
      firstName: "Laxminarayana"
      lastName: "Boga"
      email: "test@test.com"
      street: "test street"
      city: "test city"
      subjectsLearning: [
        { marksObtained: 70, subjectName: "MySQL" }
        { marksObtained: 100, subjectName: "Java" }
        { marksObtained: 90, subjectName: "MongoDB" }
      ]
    }
  ) {
    id
    firstName
    lastName
    email
    street
    city
    learningSubjects(subjectNameFilter: All) {
      id
      subjectName
      marksObtained
    }
    fullName
  }
}

```


### mutation with variables

```
mutation createStudentRequest($createStudentRequest: CreateStudentRequest) {
  createStudent(
    createStudentRequest: $createStudentRequest
  ) {
    id
    firstName
    lastName
    email
    street
    city
    learningSubjects(subjectNameFilter: All) {
      id
      subjectName
      marksObtained
    }
    fullName
  }
}

================

variables:

{
  "createStudentRequest": {
      "firstName": "abcd",
      "lastName": "efgh",
    
      "email": "test@test.com",
      "street": "test street",
      "city": "test city",
      "subjectsLearning": [
        { "marksObtained": 70, "subjectName": "MySQL" },
        { "marksObtained": 100, "subjectName": "Java" },
        { "marksObtained": 90, "subjectName": "MongoDB" }
      ]
   
    
  }
}
```