# NAME

Template::LiquidX::Tag::Dump - Simple Perl Structure Dumping Tag (Functioning Custom Tag Example)

# Synopsis

    use Template::Liquid;
    use Template::LiquidX::Tag::Dump;
    print Template::Liquid->parse("{%dump var%}")->render(var => [qw[some sort of data here]]);

# Description

This is a dead simple demonstration of
[extending Template::Liquid](https://metacpan.org/pod/Template::Liquid#Extending-Template::Liquid).

This tag attempts to use [Data::Dump](https://metacpan.org/pod/Data::Dump) and [Data::Dumper](https://metacpan.org/pod/Data::Dumper) to create
stringified versions of data structures...

    use Template::Liquid;
    use Template::LiquidX::Tag::Dump;
    warn Template::Liquid->parse("{%dump env%}")->render(env => \%ENV);

...or the entire current scope with `.`...

    use Template::Liquid;
    use Template::LiquidX::Tag::Include;
    warn Template::Liquid->parse('{%dump .%}')
        ->render(env => \%ENV, inc => \@INC);

...or the entire stack of scopes with `.*`...

    use Template::Liquid;
    use Template::LiquidX::Tag::Include;
    warn Template::Liquid->parse('{%for x in (1..1) %}{%dump .*%}{%endfor%}')
        ->render();

# Notes

This is a 5m hack and is subject to change ...I've included no error handling
and it may be completly broken. For a better example, see
[Template::LiquidX::Tag::Include](https://metacpan.org/pod/Template::LiquidX::Tag::Include).

# See Also

Liquid for Designers: http://wiki.github.com/tobi/liquid/liquid-for-designers

[Template::Liquid](https://metacpan.org/pod/Template::Liquid#Extending-Template::Liquid)'s section on
custom tags.

# Author

Sanko Robinson &lt;sanko@cpan.org> - http://sankorobinson.com/

# License and Legal

Copyright (C) 2009-2016 by Sanko Robinson &lt;sanko@cpan.org>

This program is free software; you can redistribute it and/or modify it under
the terms of The Artistic License 2.0.  See the `LICENSE` file included with
this distribution or http://www.perlfoundation.org/artistic\_license\_2\_0.  For
clarification, see http://www.perlfoundation.org/artistic\_2\_0\_notes.

When separated from the distribution, all original POD documentation is
covered by the Creative Commons Attribution-Share Alike 3.0 License.  See
http://creativecommons.org/licenses/by-sa/3.0/us/legalcode.  For
clarification, see http://creativecommons.org/licenses/by-sa/3.0/us/.
