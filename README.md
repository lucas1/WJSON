WJSON
===========

Write JSON with simplicities

## INSTALL

$ cpan App::cpanminus

$ cpanm git://github.com/lucas1/WJSON.git

## SYNOPSIS

        use WJSON;
        
        my $json = new WJSON;
        $json->Object(
           key_1 => 'value_1',
           key_2 => 'value_2',
           key_3 => 'value_3',
        );
        print $json->Print;
        
## ATTRIBUTES

#### encoding
set encoding, default utf-8

#### variable
set variable and return: var get_variable = {}

## METHODS

#### Open
Open object or array

#### Close
Close object or array

#### Object
Create object with prototyped set of key/value (properties)

#### HashObject
Create hash object with prototyped set of {key/value} (properties)

#### Array
Create array, set of value

#### Header
Return "application/json"

#### HeaderJS
Return "application/javascript"

#### HeaderCGI
Return "Content-type: application/json\n\n"

#### HeaderJSCGI
Return "Content-type: application/javascript\n\n"

#### Print
Print JSON


## EXAMPLES

#### Example 1

        my $json = new WJSON(encoding => 'iso-8859-1');
        $json->Array('value_1', 'value_2', 'value_3');
        print $json->Print;

###### Return JSON

        ["value_1", "value_2", "value_3"]
        
#### Example 2

           my $json = new WJSON;
           $json->encoding('iso-8859-1');
           $json->Object(
               key_1 => 'value_1',
               key_2 => 'value_2',
               key_3 => 'value_3',
           );
           print $json->Print;

###### Return JSON

           {
               "key_3": "value_3",
               "key_1": "value_1",
               "key_2": "value_2"
           }

#### Example 3

           my $json = new WJSON;
           $json->HashObject(
               {
                   key_1 => 'value_1',
                   key_2 => 'value_2',
                   key_3 => 'value_3',
               }
           );
           print $json->Print;
           
###### Return JSON

           [{
               "key_3": "value_3",
               "key_1": "value_1",
               "key_2": "value_2"
           }]
           
#### Example 4

           my $json = new WJSON;
           $json->Open('Data');
               $json->Object(
                   key_1 => 'value_1',
                   key_2 => 'value_2',
                   key_3 => 'value_3',
               );
           $json->Close;
           print $json->Print;
           
###### Return JSON

           {
               "Data": {
                   "key_3": "value_3",
                   "key_1": "value_1",
                   "key_2": "value_2"
               }
           }

#### Example 5

           my $json = new WJSON;
           $json->Open('Data');
               $json->Object(
                   key_1 => 'value_1',
                   key_2 => 'value_2',
                   key_3 => 'value_3',
               );
               $json->Object(
                   key_1 => 'value_1',
                   key_2 => 'value_2',
                   key_3 => 'value_3',
               );
           $json->Close;
           print $json->Print;
           
###### Return JSON

           {
               "Data": [{
                   "key_3": "value_3",
                   "key_1": "value_1",
                   "key_2": "value_2"
               }, {
                   "key_3": "value_3",
                   "key_1": "value_1",
                   "key_2": "value_2"
               }]
           }

#### Example 6

           my $json = new WJSON;
           $json->Open('Data');
               $json->Array('value_1', 'value_2', 'value_3');
           $json->Close;
           print $json->Print;

           
###### Return JSON

           {
               "Data": ["value_1", "value_2", "value_3"]
           }

## Example 7

           my $json = new WJSON;
           $json->Object(
               key_1 => 'value_1',
               key_2 => 'value_2',
               key_3 => 'value_3',
           );
           $json->Object(
               key_1 => 'value_1',
               key_2 => 'value_2',
               key_3 => 'value_3',
           );
           $json->Open('Data');
               $json->Open('SubData');
                   $json->Object(
                       key_1 => 'value_1',
                       key_2 => 'value_2',
                       key_3 => 'value_3',
                   );
                   $json->Object(
                       key_1 => 'value_1',
                       key_2 => 'value_2',
                       key_3 => 'value_3',
                   );
               $json->Close;
               $json->Array(['value_1', 'value_2', 'value_3'], ['value_4', 'value_5']);
               $json->Array(['value_6', 'value_7']);
           $json->Close;
           $json->Array(['value_1', 'value_2', 'value_3'], ['value_4', 'value_5']);
           print $json->Print;
           
###### Return JSON

           [{
                   "key_3": "value_3",
                   "key_1": "value_1",
                   "key_2": "value_2"
               }, {
                   "key_3": "value_3",
                   "key_1": "value_1",
                   "key_2": "value_2",
                   "Data": [{
                           "SubData": [{
                               "key_3": "value_3",
                               "key_1": "value_1",
                               "key_2": "value_2"
                           }, {
                               "key_3": "value_3",
                               "key_1": "value_1",
                               "key_2": "value_2"
                           }]
                       },
                       ["value_1", "value_2", "value_3"],
                       ["value_4", "value_5"], "value_6", "value_7"
                   ]
               },
               ["value_1", "value_2", "value_3"],
               ["value_4", "value_5"]
           ]
           
#### Example 8

            my $json = new WJSON;
            $json->variable('json');
            $json->Object(
                key_1 => 'Formulário',
                key_2 => 'value_2',
                key_3 => 'value_3',
            );
            print $json->Print;

           
###### Return JSON

            var json = {
                "key_3": "value_3",
                "key_1": "Formulário",
                "key_2": "value_2"
            }

## AUTHOR
Lucas Tiago de Moraes, <lucastiagodemoraes@gmail.com>


           
           
           
           
           
           
           
           
           






















































