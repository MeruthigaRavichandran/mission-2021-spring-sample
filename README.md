# Spring Boot Sample Project

## Installation (if not already installed)

* Install Java
* Install Maven
* Install IntelliJ Idea community Edition
* Install Postman tool

## Getting started with Spring Boot application

* Go to https://start.spring.io website
* Refer below image for sample configuration

![Start Spring IO Image](https://i.ibb.co/gMVkqbg/Screenshot-2020-08-06-at-10-10-40-PM.png)

* Click on *Generate*
* Extract the downloaded Zip file
* Open IntelliJ Idea & Click on *Import Project*
* Navigate to the extracted Zip folder & click on pom.xml
* Click import


**Now you are ready for development**

## Code Explanation

### How to create Controller

* Create a class E.g. MyController
* Annotate the class with @RestController
* Create method & annotate it with @RequestMapping(value="/test")

* If you want text/plain as **Content-Type** header, return **String**
* If you want application/json as **Content-Type** header, return either **Map** or Java Object like Person

### Sample Controller

```java
import org.springframework.web.bind.annotation.RequestMapping;
import org.springframework.web.bind.annotation.RestController;

import java.util.ArrayList;
import java.util.HashMap;
import java.util.List;
import java.util.Map;

@RestController
public class ItechController {

    // Content-Type text/plain
    @RequestMapping(value = "/test")
    public String test() {
        return "Hello world !";
    }

    // Content-Type application/json
    @RequestMapping(value = "/test-json")
    public Map testJson(){
        Map<String, Object> map = new HashMap<>();
        map.put("name", "Vicky");
        map.put("city", "Thiruvarur");
        map.put("workplace", "Chennai");
        map.put("pincode", 610001);

        return map;
    }

    // Content-Type application/json
    @RequestMapping(value = "/vicky")
    public Person getVicky() {
        Address address = new Address();
        address.city = "thiruvarur";
        address.state = "tamil nadu";
        address.pincode = 610001;

        List<String> languages = new ArrayList<>();
        languages.add("ta");
        languages.add("en");
        languages.add("hi");

        Person person = new Person();
        person.id = 1;
        person.name = "Vicky";
        person.address = address;
        person.languages = languages;

        return person;
    }
}
```
### To test the application

* Start the application by right click & run the class with public static void main() method

* Once its started, go to postman tool & try hitting any of the endpoint

E.g. 

```
http://localhost:8080/test

http://localhost:8080/test-json

http://localhost:8080/vicky
```
