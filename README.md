# CSV <3 YAML Format
 

_CSV (Line-by-Line) Records with YAML Encoding Rules - A Modern (Simple) Tabular Data Format incl. Arrays, Numbers, Booleans, Nulls, Nested Structures, Comments and More_



## CSV <3 YAML By Example


```
# "Vanilla" CSV <3 YAML

1,John,12 Totem Rd. Aspen,true
2,Bob,null,false
3,Sue,"Bigsby, 345 Carnival, WA 23009",false
```

or

```
# "Vanilla" CSV <3 YAML (Pretty Printed)

1, John, 12 Totem Rd. Aspen,               true
2, Bob,  null,                             false
3, Sue,  "Bigsby, 345 Carnival, WA 23009", false
```

or

```
# CSV <3 YAML with header / headers row

id,name,address,regular
1,John,12 Totem Rd. Aspen,true
2,Bob,null,false
3,Sue,"Bigsby, 345 Carnival, WA 23009",false
```

or

```
# CSV <3 YAML with values containing quotes and commas

id,name,address,regular
1,John,"12 Totem Rd., Aspen",true
2,Bob,null,false
3,Sue,"\"Bigsby\", 345 Carnival, WA 23009",false
```

or

```
# CSV <3 YAML with array values

1,directions,[north,south,east,west]
2,colors,[red,green,blue]
3,drinks,[soda,water,tea,coffe]
4,spells,[]
```	

or

```
# CSV <3 YAML with all kinds of values

index,value1,value2
number,1,2
boolean,false,true
"null",null,non null
array of numbers,[1],[1,2]
simple object,{a:1},{a:1, b:2}
array with mixed objects,[1,null,ball],[2,{a:10,b:20},cube]
string with quotes,"a\"b","alert(\"Hi!\")"
string with bell&newlines,"bell is \u0007","multi\nline\ntext"
```



## Frequently Asked Questions (FAQ) and Answers

### Q: What's the recommended file type extension for CSV <3 YAML files?

The recommended file format for CSV <3 YAML files is `.csv` :-) or use `.yaml.csv` (to highlight 
the fact of the YAML encoding rules).





## Do-It-Yourself (DIY) - No CSV <3 YAML Parser in Your Language? - Build Your Own 


Build your own parser:

- Read the input (e.g. string or file) line-by-line
  - If the line is blank (only whitespace), skip the line.
  - If the line starts with a hash mark (`#`), skip the comment line.
  - Otherwise wrap the line in (`[]`) and pass along to the YAML parser :-).
  
  
Example in Ruby:

``` ruby
def parse( input )
   records = []
   input.each_line do |line|
        
      ##  note: chomp('') if is an empty string,
      ##    it will remove all trailing newlines (e.g. \n or \r\n) from the line
      line = line.chomp( '' )
      
      ##  strip leading and trailing whitespaces (space and tab)
      line = line.strip
      
      next if line.empty?             ## skip blank lines
      next if line.start_with?( '#' ) ## skip comment lines
        
      ## note: auto-wrap in array e.g. with []
      records << YAML.load( "[#{line}]" )
    end
    records
end
```



## Inspiration / Heritage / Alternatives

### JSON

- CSV <3 JSON Format, see <https://github.com/csv11/csv-json>



## License

The CSV <3 YAML format is dedicated to the public domain.
