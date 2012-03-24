# NAME

Python::Bytecode::SAX - Process Python bytecode, generating SAX events.

# SYNOPSIS

    use Python::Bytecode::SAX;
    use XML::SAX::Writer;
    my $handler = XML::SAX::Writer->new( Output => 'foo.xml' );
    my $parser = Python::Bytecode::SAX->new( Handler => $handler, SAX => 2 );
    $parser->parse_file('foo.pyc');

Or

    use Python::Bytecode::SAX;
    use XML::Handler::YAWriter;
    my $handler = XML::Handler::YAWriter->new(
        AsFile => 'foo.xml',
        Pretty  => {
            CompactAttrIndent  => 1,
            PrettyWhiteIndent  => 1,
            PrettyWhiteNewline => 1,
            CatchEmptyElement  => 1
        }
    );
    my $parser = Python::Bytecode::SAX->new( Handler => $handler, SAX => 1 );
    $parser->parse_file('foo.pyc');

# DESCRIPTION

This module reads and decodes a Python bytecode file, generating SAX1 or SAX2
events (SAX1 is the default) for what it finds.

Until more documentation is written, you can examine the two XML files generated
in the `t/` directory by `make test` to get a feel for the overal structure and
the element and attribute names.

# HISTORY

Based on the [Python::Bytecode](http://search.cpan.org/perldoc?Python::Bytecode) module by Simon Cozens <simon@cpan.org>,
which is based on the `dis.py` file in the Python Standard Library.

# SEE ALSO

[Python::Bytecode](http://search.cpan.org/perldoc?Python::Bytecode) by Simon Cozens <simon@cpan.org>.

# AUTHOR

Gregor N. Purdy, Sr. <gnp@acm.org<gt>

# COPYRIGHT

Copyright (C) 2003-2012 Gregor N. Purdy, Sr. All rights reserved.

# LICENSE

This program is free software. Its use is subject to the same license as Perl.