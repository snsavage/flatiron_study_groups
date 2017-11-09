# Debugging with Pry

## Getting Started
Add `gem pry` or `gem pry-rails` to `./Gemfile`.  Run `bundle install`.

Depending on the type of project add this to the top of your file:
```
require ‘pry’
```

In your code add `binding.pry` to set a breakpoint.  The syntax `<object>.pry` can also be used. 

## Basics
Pry provides a REPL allowing you to interact with you code as it runs.

For instance adding `binding.pry` to this class will pause my application when the `#foods` method is called on the `NutritionIx` class.
```ruby
class NutritionIx
  include HTTParty

  ALLOWED_KEYS = [
	  ...
  ].freeze

  attr_accessor :search, :line_delimited

  def initialize(search = '', line_delimited = true)
    self.class.base_uri 'https://trackapi.nutritionix.com'
    @search = search
    @line_delimited = line_delimited
  end

  ...

  def foods
	  binding.pry
    return [] if errors?

    parse_foods
  end

  ...
end
```

Pry  provides a prompt that looks like this:
```
From: /Users/snsavage/Development/carb_tracker/app/models/nutrition_ix.rb @ line 41 NutritionIx#foods:

    40: def foods
 => 41:   binding.pry
    42:   return [] if errors?
    43:
    44:   parse_foods
    45: end

[1] pry(#<NutritionIx>)>
```

From here Pry provides a number of ways to interact with the code:
```
[4] pry(#<NutritionIx>)> @search
=> "1 apple \n 1 banana"
``` 

## Pry Basics
### Entering Input
```
pry(main)> !			# Clear input buffer.
pry(main)> ;			# Suppress evaluation output.
pry(main)> hist --tail <number>      # Show last <number> history entries. 
pry(main)> hist -n --tail <number>   # Remove line numbers. 
pry(main)> play -l <number>          # Play line number.
pry(main)> play -l A..B              # Play range of lines.
pry(main)> exit		          # Exit current context.
pry(main)> exit!			      # Exit program.
pry(main)> _      # Last result local.
pry(main)> _ex_   # Last exception.
pry(main)> whereami   # Redisplay current code.
pry(main)> pry-backtrace  # Backtrace to current context.
pry(main)> ? <command>   # Pry help system.
```

### State Navigation
```
pry(main)> cd <object>     # Change scope.
pry(main)> cd ..           # Back to previous scope.
pry(main)> ls              # View current context.
```

`ls` wraps Ruby introspection methods including `methods`, `instance_variables`, `constants`, `local_variables`, `instance_methods`, `class_variables`, etc.

`ls` options:
```
-m, --methods        Show public methods defined on the Object (default).
-M, --module         Show methods defined in a Module or Class.
-p, --ppp            Show public, protected and private methods.
-q, --quiet          Show only methods defined on object.singleton_class and object.class.
-v, --verbose        Show methods and constants on all super-classes.
-g, --globals        Show global variables, including those builtin to Ruby.
-l, --locals         Show locals, including those provided by Pry.
-c, --constants      Show constants.  
-i, --ivars          Show instance variables and class variables.
```

Example `ls` output:
```
[9] pry(#<NutritionIx>)> ls
ActiveSupport::ToJsonWithActiveSupportEncoder#methods: to_json
NutritionIx#methods:
  data  errors?  foods  line_delimited  line_delimited=  messages  reload!  search  search=
instance variables: @data  @line_delimited  @search
locals: _  __  _dir_  _ex_  _file_  _in_  _out_  _pry_
[10] pry(#<NutritionIx>)>
```

```
pry(main)> find-method <method-name>   # Find a method in the source code.
pry(main)> find-method <method-name> -c   # Search source code.
pry(main)> nesting     # Currently open context and nesting.
```

### Source Browsing
```
pry(main)> show-source <name>   # Show source. 
pry(main)> show-source          # Show source for current context.
pry(main)> show-source <pry command>   # Show source for pry command.
pry(main)> show-source <name> -a   # Show source with monkey patches.
pry(main)> show-doc      # Show documentation.
```




