# quick-json Parser #

quick-json is a Java library that can be used to convert Java Objects into their JSON representation. It can also be used to convert a JSON string to an equivalent Java object. quick-json can work with any arbitrary Java objects.

### Maven Dependency ###

```
<dependency>
    <groupId>com.codesnippets4all</groupId>
    <artifactId>quick-json</artifactId>
    <version>1.0.4</version>
</dependency>
```


Official blog of quick-json parser and related technical articles.

<a href='http://www.codesnippets4all.com/'><a href='http://www.codesnippets4all.com/'>http://www.codesnippets4all.com/</a></a><br />

This parser supports validating/non-validating versions.

Non-Validating parser verifies the standards of json while parsing and will not validate keys/values and will not apply any custom validations at all.

Validating parser version is a strict parser and it does parsing based upon pre-configured validation rules.

This Parser is a simple and flexible parser for parsing input JSON string and return the corresponding java collection representation.

**e.g.**

```
{
   "key1": "value1",
   "key2": "value2",
   "key3": "value3"
}
```

Now Map generated out of the above mentioned JSON String will look like,

A map with one key as 'samplejson' and its value as another map of key/value pairs. i.e. it will be very easy for the developers to look up for a specific key within json hierarchy.

Value can be looked up by just parsing the above JSON string using parsing API as follows,

```
 JsonParserFactory factory=JsonParserFactory.getInstance();
 JsonParser parser=factory.newJsonParser();
 Map jsonData=parser.parse(inputJsonString);

 String value=(String)jsonData.get("key2");
```

Simple examples of json,

**E.g.1**
```
[{
"key":"value",
"key1":[234234.32,adfasdf],
"key2":[arrayvalue,arrayvalue1,arrayvalue2]
},
{
"key":{
        subjsonkey:subjsonvalue
        }
},
"Rajesh Putta",
234234.23]
```

<br>
<b>E.g.2</b>
<pre><code>JSON:

{
    "glossary": {
        "title": "example glossary",
		"GlossDiv": {
            "title": "S",
			"GlossList": {
                "GlossEntry": {
                    "ID": "SGML",
					"SortAs": "SGML",
					"GlossTerm": "Standard Generalized Markup Language",
					"Acronym": "SGML",
					"Abbrev": "ISO 8879:1986",
					"GlossDef": {
                        "para": "A meta-markup language, used to create markup languages such as DocBook.",
						"GlossSeeAlso": ["GML", "XML"]
                    },
					"GlossSee": "markup"
                }
            }
        }
    }
}
</code></pre>
<br>
<b>E.g.3</b>
<pre><code>JSON:

{"menu": {
  "id": "file",
  "value": "File",
  "popup": {
    "menuitem": [
      {"value": "New", "onclick": "CreateNewDoc()"},
      {"value": "Open", "onclick": "OpenDoc()"},
      {"value": "Close", "onclick": "CloseDoc()"}
    ]
  }
}}
</code></pre>
<br>
<b>E.g.4</b>
<pre><code>JSON:

{"widget": {
    "debug": "on",
    "window": {
        "title": "Sample Konfabulator Widget",
        "name": "main_window",
        "width": 500,
        "height": 500
    },
    "image": { 
        "src": "Images/Sun.png",
        "name": "sun1",
        "hOffset": 250,
        "vOffset": 250,
        "alignment": "center"
    },
    "text": {
        "data": "Click Here",
        "size": 36,
        "style": "bold",
        "name": "text1",
        "hOffset": 250,
        "vOffset": 100,
        "alignment": "center",
        "onMouseUp": "sun1.opacity = (sun1.opacity / 100) * 90;"
    }
}}   
</code></pre>

<h3>quick-json features</h3>

# Compliant with JSON specification (RFC4627) <br><br>
# High-Performance JSON parser  <br><br>
# Supports Flexible/Configurable parsing approach  <br><br>
# Configurable validation of key/value pairs of any JSON Heirarchy  <br><br>
# Easy to use  # Very Less foot print <br><br>
# Raises developer friendly and easy to trace exceptions <br><br>
# Pluggable Custom Validation support - Keys/Values can be validated by configuring custom   validators as and when encountered <br><br>
# Validating and Non-Validating parser support <br><br>
# Support for two types of configuration (JSON/XML) for using quick-json validating parser <br><br>
# Require JDK 1.5 (1.5.0_22_1) # No dependency on external libraries <br><br>
# Support for Json Generation through object serialization <br><br>
# Support for collection type selection during parsing process <br><br>


<h1>quick-json Non-Validating parser Usage</h1>

quick-json Non-Validating parser supports parsing of different formats of json strings which are compliant with JSON spec. Parser throws developer friendly exceptions in case of there is any syntax/semantic issues.<br>
<br>
<b>E.g.</b>

<pre><code> samplejson = {
   "key1": value1,
   "key_2": "value2",
   key3: value3,
   key4:234234234,
   key5:234234.233
}
</code></pre>

Value can be looked up by just parsing the above JSON string using parsing API as follows,<br>
<br>
<pre><code> JsonParserFactory factory=JsonParserFactory.getInstance();
 JsonParser parser=factory.newJsonParser();
 Map jsonData=parser.parseJson(inputJsonString);

 //lookup the key 'key_2' under Json Block 'samplejson'
 String value=jsonData.get("samplejson").get("key_2");
</code></pre>



<pre><code>{
"employees": [
{ "firstName":"Rajesh" , "lastName":"Putta" }, 
{ "firstName":"Rajesh" , "lastName":"P" }, 
{ "firstName":"first name" , "lastName":"last name" }
]
}
</code></pre>


Value can be looked up by just parsing the above JSON string using parsing API as follows,<br>
<br>
<pre><code> JsonParserFactory factory=JsonParserFactory.getInstance();
 JsonParser parser=factory.newJsonParser();
 Map jsonData=parser.parseJson(inputJsonString);

Map rootJson=jsonData.get("root");
 List al=rootJson.get("employees");
 String fName=((Map)al.get(0)).get("firstName");
 String lName=((Map)al.get(0)).get("lastName");
</code></pre>

<br><br>

<h1>quick-json Validating parser Usage</h1>

quick json validating parser can be used whenever json has to be validated at every level to see if the format is expected or not. Keys/Values, Sub-Json, Array and its elements can be validated.<br>
<br>
What/When/Where needs to be validated ? All this information is expected to be passed to the parser during initialization.<br>
<br>
Below is the sample way of initializing and working with validating parser.<br>
<br>
<pre><code> JsonParserFactory factory=JsonParserFactory.getInstance();
 JsonParser parser=factory.newJsonParser();

//initialize parser with the json validation configuration file stream
 parser.initialize(xml_stream));
			
//configure parser for validating
 parser.setValidating(true);

//parse input json string with validating parser instance
 Map jsonData=parser.parseJson(inputJsonString);

</code></pre>


<b>E.g.1</b>

<b>Input JSON String</b>

<pre><code>sample={
"key":"value",
"key1":"value1",
"key2":234234234
}
</code></pre>

Validation configuration for the above JSON string would be,<br>
<br>
<pre><code>&lt;json-config&gt;
	&lt;json-heirarchy path="root"&gt;
		&lt;KeyValues&gt;
			&lt;KeyValue name="ROOT" valueType="JSON"/&gt;
		&lt;/KeyValues&gt;
	&lt;/json-heirarchy&gt;

	&lt;json-heirarchy path="sample"&gt;
		&lt;KeyValues&gt;
			&lt;KeyValue name="default" valueType="STRING_LITERAL"/&gt;
			&lt;KeyValue name="key2" valueType="INTEGER"/&gt;
		&lt;/KeyValues&gt;
	&lt;/json-heirarchy&gt;
	
&lt;/json-config&gt;
</code></pre>


<b>root</b> configuration is for validating the root level, this is mandatory to validate the root level is JSON/JSON_ARRAY<br>
<br>
<b>sample</b> configuration is for the key/value pairs under sample json string. As per the above configuration, <b>default</b> configuration is applicable for all the key/value pairs whenever there is no specific validation configured for keys. In this case <b>key2</b> requirement is to have separate validation configuration. so overriding the default one.<br>
<br>
<b>Validation data types</b>

<table><thead><th>JSON </th><th> validates for JSON presence</th></thead><tbody>
<tr><td>JSON_ARRAY </td><td> validates for JSON_ARRAY presence</td></tr>
<tr><td>STRING_LITERAL </td><td> validates for double quoted string presence</td></tr>
<tr><td>STRING </td><td> Validates for simple string with alphanumeric data</td></tr>
<tr><td>INTEGER </td><td> Validates for number data, doesnt allow double type of values</td></tr>
<tr><td>DOUBLE </td><td> Validates for number data, allows double type of values</td></tr>
<tr><td>BOOLEAN </td><td> Validates for boolean value (true or false)</td></tr>
<tr><td>NULL </td><td> Validates for null         </td></tr></tbody></table>



<b>E.g.2</b>

<b>Input JSON String</b>

<pre><code>sample={
"key":"value",
"key1":["value1",234234.32,adfasdf],
"key2":234234234
}
</code></pre>

Validation Configuration for the above json string would be,<br>
<br>
<pre><code>&lt;json-config&gt;
	&lt;json-heirarchy path="root"&gt;
		&lt;KeyValues&gt;
			&lt;KeyValue name="ROOT" valueType="JSON"/&gt;
		&lt;/KeyValues&gt;
	&lt;/json-heirarchy&gt;

	&lt;json-heirarchy path="sample"&gt;
		&lt;KeyValues&gt;
			&lt;KeyValue name="default" valueType="STRING_LITERAL"/&gt;
			&lt;KeyValue name="key1" valueType="JSON_ARRAY"/&gt;
			&lt;KeyValue name="key2" valueType="INTEGER"/&gt;
		&lt;/KeyValues&gt;
	&lt;/json-heirarchy&gt;
	
	&lt;json-heirarchy path="sample/key1"&gt;
		&lt;KeyValues&gt;
			&lt;KeyValue name="default" valueType="STRING_LITERAL"/&gt;
			&lt;KeyValue index="1" valueType="DOUBLE"/&gt;
			&lt;KeyValue index="2" valueType="STRING"/&gt;
		&lt;/KeyValues&gt;
	&lt;/json-heirarchy&gt;	
	
&lt;/json-config&gt;
</code></pre>
<br><br>

<h1>quick-json Validating parser Usage - with JSON based validation configuration</h1>

quick json validating parser can be configure with JSON based validation configuration  whenever other json has to be validated at every level to see if the format is expected or not. Keys/Values, Sub-Json, Array and its elements can be validated.<br>
<br>
What/When/Where needs to be validated ? All this information is expected to be passed to the parser during initialization.<br>
<br>
Below is the sample way of initializing and working with validating parser with JSON based validation configuration.<br>
<br>
<pre><code>JsonParserFactory factory=JsonParserFactory.getInstance();

JSONParser parser=factory.newJsonParser(ValidationConfigType.JSON);
			
parser.initializeWithJson(json_based_validation_config_stream);
			
parser.setValidating(true);

//parse input json string with validating parser instance
Map jsonData=parser.parseJson(inputJsonString);

</code></pre>

<b>E.g.1</b>

<pre><code>[{
"key":"value",
"key1":[234234.32,true ],
"key2":[arrayvalue,arrayvalue1,arrayvalue2]
},
{
"key":{
	subjsonkey:subjsonvalue
	}
},
"Rajesh Putta",
234234.23]
</code></pre>

Below would be the JSON based validation configuration,<br>
<br>
<pre><code>{
	"root":{
		"ROOT":{valueType:"JSON_ARRAY"},
		"0":{valueType:"JSON"},
		"1":{valueType:"JSON"},
		"2":{valueType:"STRING_LITERAL"},
		"3":{valueType:"DOUBLE"}
	},
	"root[0]":{
		"key1":{valueType:"JSON_ARRAY"},
		"key2":{valueType:"JSON_ARRAY"}
	},
	"root[1]":{
		"key":{valueType:"JSON"}
	},
	"root[0]/key1":{
		"0":{valueType:"DOUBLE"},
		"1":{valueType:"BOOLEAN"}
	},
	"root[0]/key2":{
		"default":{valueType:"STRING"}
	},
	"root[1]/key":{
		"default":{valueType:"STRING"}
	},
}
</code></pre>



<br><br>
<h1>Json Generator Usage</h1>

JSONGenerator helps in serializing the java objects to JSON format.<br>
<br>
- Supports serialization of Classes, Arrays, Map, List, Set, Properties, String, Date, Integer, Float, Double, Boolean, etc types of data<br>
<br>
- Strictly adheres to the JSON spec during serialization process<br>
<br>
<b>E.g.</b>

Here is the example data set hierarchy to be serialized to JSON format,<br>
<br>
<pre><code>		Map data=new HashMap();
		
		Properties prop=new Properties();
		
		prop.setProperty("1", "1");
		prop.setProperty("2", "2");
		prop.setProperty("3", "3");
		
		data.put("name", "Rajesh Putta");
		data.put("age", 28);
		data.put("city", new StringBuilder("hyderabad"));
		data.put("subdata", prop);
		data.put("array", new int[]{234,555,777,888});
		data.put("chararray", new char[]{'a','b','c'});
		data.put("doublearray", new double[]{234,555,777,888});
		data.put("floatarray", new byte[]{1,2,34,35});

		Map submap=new HashMap();
		submap.put(1, 10);
		submap.put(2, 20);		
		
		TestPojo tp=new TestPojo();
		
		tp.setAge(28);
		tp.setName("Rajesh");
		tp.setSs(3223.33);
		tp.setData(submap);		
		
		Set set=new HashSet();
		set.add(234);
		set.add(2343);
		set.add("asdfasfd");
		set.add(tp);
		

		data.put("set-pojo", set);
		

		data.put("objectarray", new Object[]{submap,set,submap,tp});
</code></pre>


Here is the implementation for serializing the above data set<br>
<br>
<pre><code>		JsonGeneratorFactory factory=JsonGeneratorFactory.getInstance();
		JSONGenerator generator=factory.newJsonGenerator();
		String json=generator.generateJson(data);
</code></pre>

Here is the serialized data object,<br>
<br>
<pre><code>[{"age":28,"doublearray":[234.0,555.0,777.0,888.0],"floatarray":[1,2,34,35],"set-pojo":["asdfasfd",{"name":"Rajesh","age":28,"ss":3223.33,"data":{"2":20,"1":10},},2343,234],"subdata":{"3":"3","2":"2","1":"1"},"objectarray":[{"2":20,"1":10},{"2":20,"1":10},{"name":"Rajesh","age":28,"ss":3223.33,"data":{"2":20,"1":10},}],"name":"Rajesh Putta","chararray":[a,b,c],"city":"hyderabad","array":[234,555,777,888]}]
</code></pre>