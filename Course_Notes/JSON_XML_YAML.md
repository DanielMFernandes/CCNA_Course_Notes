# 60. JSON, XML, AND YAML

DATA SERIALIZATION

- Data Serialization is the process of converting data into a standardized format/structure that can be stored (in a file) or transmitted (over a network) and reconstructed later (ie: by a different application)
    - This allows the data to be communicated between applications in a way both applications understand.

- Data Serialization languages allow us to represent *variables* with text

![image](https://github.com/psaumur/CCNA/assets/106411237/f09eeeba-7779-40c8-af18-f1227bf0cf47)

---

JSON (JAVASCRIPT OBJECT NOTATION)

- JSON (JavaScript Object Notation) is an open standard file format and data interchange format that uses human-readable text to store and transmit data objects

- It is standardized in RFC 8259 (https://datatracker.ietf.org/doc/html/rfc8259)
- It was derived from JavaScript, but it is language-independent and many modern programming languages are able to generate and read JSON data
    - REST APIs often use JSON
- *Whitespace* is insignificant

- JSON can represent four “primitive” data Types:
    - String
    - Number
    - Boolean
    - Null

- JSON also has two “structured” data Types:
    - Object
    - Array

---

JSON PRIMITIVE DATA TYPES:

- A string is a text value. It is surrounded by double quotes “ “
    - “Hello”
    - “Five”
    - “5”

- A number is a numeric value. It is not surrounded by quotes
    - 5
    - 100
    
- A boolean is a data type that has only two possible values, not surrounded by quotes
    - true
    - false

- A null value represents the intentional absence of any object value. It is not surrounded by quotes
    - null

---

JSON STRUCTURED DATA TYPES:

- An OBJECT is an unordered list of *key-value pairs* (variables)
    - Sometimes called a dictionary
    - Objects are surrounded by curly brackets {}
    - The *key* is a string
    - The *value* is any valid JSON data type (string, number, boolean, null, object, array)
    - The *key* and *value* are separated by a colon :
    - If there are multiple key-value pairs, each pair is separated by a comma

![image](https://github.com/psaumur/CCNA/assets/106411237/24a15571-bb9f-43b4-889f-69f23ffb91bc)

![image](https://github.com/psaumur/CCNA/assets/106411237/b66f041d-2449-43f0-8a04-2c0da5391411)

![image](https://github.com/psaumur/CCNA/assets/106411237/54d69eed-4369-4ef6-a437-6b5ecce14586)

- An array is a series of *values* separated by commas
    - Not *key-value pairs*
    - The values do not have to be the same data type

![image](https://github.com/psaumur/CCNA/assets/106411237/3212f472-f966-49e5-9b9a-7bedcfe47487)

![image](https://github.com/psaumur/CCNA/assets/106411237/f8075e93-2be7-4b2e-a2af-968961bbc5a7)

---

XML (EXTENSIBLE MARKUP LANGUAGE)

- XML (EXTENSIBLE MARKUP LANGUAGE) was developed as a markup language, but is now used as a general data serialization language
    - Markup languages (ie: HTML) are used to format text (font, size, color, headings, etc)
    - XML is generally less human-readable than JSON
    - Whitespace is insignificant
    - Often used by REST APIs
    - The format is "`<key> value </key>`" (similar to HTML)

![image](https://github.com/psaumur/CCNA/assets/106411237/f954b0ef-f563-4536-94c8-334b6d8f97c6)

![image](https://github.com/psaumur/CCNA/assets/106411237/948dae9e-b59b-4607-8e6d-b39837baba70)

---

YAML (YAML AIN’T MARKUP LANGUAGE)

- YAML originally meant *Yet Another Markup Language* but to distinguish its purpose as a data-serialization language rather than a markup language, it was repurposed to *YAML Aint Markup Language*
- YAML is used by the network automation tool Ansible (covered later in the course)
- YAML is very human-readable
- Whitespace **is significant** (unlike JSON and XML)
    - Indentation is very important
- YAML files start with - - - (three dashes)
- - is used to indicate a list
- Keys and Values are represented as key : value

![image](https://github.com/psaumur/CCNA/assets/106411237/ecfa3659-4bc3-4596-9f11-10d2644eac1a)

Comparison between JSON and YAML using the same data

![image](https://github.com/psaumur/CCNA/assets/106411237/16e0e98b-5653-4f8a-a388-1706f91a30d4)
