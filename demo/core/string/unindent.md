## String#unindent

    require 'facets/string/unindent'

We will use these two strings as a common basis for demonstration.

    ex1 = <<-EOF.gsub(/^\s*\|/,'')
    |    I must go down to the seas again
    |      The lonely sea and the sky
    |    And all I want is a tall ship
    |      And a star to steer her by
    EOF

    ex2 = <<-EOF.gsub(/^\s*\|/,'')
    |     "Eek!"
    |  She cried
    |    As the mouse quietly scurried
    |by.
    EOF

simple examples

    "   xyz".unindent(-1).assert == "    xyz"
    "   xyz".unindent(0).assert  == "   xyz"
    "   xyz".unindent(1).assert  == "  xyz"
    "   xyz".unindent(2).assert  == " xyz"
    "   xyz".unindent(3).assert  == "xyz"
    "   xyz".unindent(4).assert  == "xyz"

large example unindented one space

    expected = <<-EOF.gsub(/^\s*\|/,'')
    |   I must go down to the seas again
    |     The lonely sea and the sky
    |   And all I want is a tall ship
    |     And a star to steer her by
    EOF

    actual = ex1.unindent(1)
    actual.assert == expected

large example unindented four spaces

    expected = <<-EOF.gsub(/^\s*\|/,'')
    |I must go down to the seas again
    |  The lonely sea and the sky
    |And all I want is a tall ship
    |  And a star to steer her by
    EOF

    actual = ex1.unindent(4)
    actual.assert == expected

unindent larger than current indention

    expected = <<-EOF.gsub(/^\s*\|/,'')
    |"Eek!"
    |She cried
    |As the mouse quietly scurried
    |by.
    EOF

    actual = ex2.unindent(100)
    actual.assert == expected

