## Custom MD Examples

The Live docs site supports Markdig extensions to enrich markdown syntax, the examples are in lin below.

[Markdig Extenstions](https://github.com/lunet-io/markdig) 

### Custom extensions

Besides default markdown syntax and markdig extnesions, we also developed some custom extension.


#### 1.Inclusion 

To include the MD file in other place and show it on current document.

syntax:

```markdown
[!include[title](pathToTheMDFile)]
```
result:


[!include[title](./SA/Index.md)]


#### 2.DrawIO 
User can include the DrawIo chart to the MD file using belowing syntax. 

```markdown
// With page index specified, the page index starts with 0
[!drawio[chartName:PageIndex](pathToTheDrawIoFile)]

// Without page index specified, default index is 0(the first page in DrawIO)
[!drawio[chartName:](pathToTheDrawIoFile)]
```
result:

[!drawio[Page index set to 1.:1](./SA/2020_7_29/5566.drawio)]

[!drawio[With default Page index.:](./SA/2020_7_29/5566.drawio)]

error result:

[!drawio[Error When Page Index is greater than Page length.:5](./SA/2020_7_29/5566.drawio)]


#### 3.Key value mapping

To map the value of the key defined in JSON file.

syntax:

```markdown
[!KeyValue[Group:Key](pathToJSONDefinitionFile)]
```
result:

[!KeyValue[table_type:B](json/info_definitions.json)]

error result:

[!KeyValue[table_type:ValueDosentExsist](json/info_definitions.json)]

[!KeyValue[GroupDosentExsist:B](json/info_definitions.json)]

### 4.Cross reference

using cross reference user can specify an unique ID at the top of MD using YAML header like belowing code:

```markdown
---
uid:UidForThisFile
name:NameForThisFile
---

content of your markdown....

```

then user can use below extension syntax to create a link to the file:

```markdown
[!xRef[TitleOfTheLink]({UidOfTheFile})]
// or use the name for the file as link text 
[!xRef[]({UidOfTheFile})]
// youcan also add anchor to the XRef
[!xRef[linkToFileE]({testA#value-objects-6})]
```

result:

[!xRef[linkToFileA]({FileA})]
[!xRef[]({FileB})]
[!xRef[linkToFileE]({FileE})]
[!xRef[linkToFileE]({testA#value-objects-6})]

error result:
[!xRef[linkToFileEWhichDoseNotExist]({FileZ})]



