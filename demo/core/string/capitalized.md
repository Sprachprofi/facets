## String#capitalized?

String#capitalized? return true if a string begins with a capitalized
letter, false otherwise.

    require 'facets/string/capitalized'

    'Abc'.assert.capitalized?

## String#downcase?

In addition String#downcase? is provided which checks to see if the
whole string is composed of lowercase letters.

    'abc'.assert.downcase?

    #'abc'.assert.lowercase?

## String#upcase?

And String#upcase? which checks to see if the whole string is composed
of uppercase letters.

    'ABC'.assert.upcase?

    #'ABC'.assert.uppercase?

