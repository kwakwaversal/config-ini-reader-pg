# NAME

Config::Pg::ServiceFile - PostgreSQL connection service file parser

# SYNOPSIS

    # ~/.pg_service.conf

    [foo]
    host=localhost
    port=5432
    user=foo
    dbname=db_foo
    password=password

    # your_program.pl

    use Config::Pg::ServiceFile;

    # {
    #     foo => {
    #         host     => 'localhost',
    #         post     => '5432',
    #         user     => 'foo',
    #         dbname   => 'db_foo',
    #         password => 'passwird',
    #     }
    # }
    my $hash_ref = Config::Pg::ServiceFile->read_file('~/.pg_service.conf');

# DESCRIPTION

[Config::Pg::ServiceFile](https://metacpan.org/pod/Config::Pg::ServiceFile) is a parser for the PostgreSQL connection service
file. The connection service file is based on the `INI` format, but uses a
`#` as the comment character. As such, this is a simple module that subclasses
[Config::INI::Reader](https://metacpan.org/pod/Config::INI::Reader), and replaces the comment character accordingly.

The accompanying module [Pg::ServiceFile](https://metacpan.org/pod/Pg::ServiceFile) provides a better interface to the
data stored in a PostgreSQL connection file. See [Pg::ServiceFile](https://metacpan.org/pod/Pg::ServiceFile) for more
information.

## METHODS

[Config::Pg::ServiceFile](https://metacpan.org/pod/Config::Pg::ServiceFile) inherits all methods from [Config::INI::Reader](https://metacpan.org/pod/Config::INI::Reader).

## read\_file

    my $hash_ref = Config::Pg::ServiceFile->read_file($filename);

Given a filename, this method returns a hashref of the contents of that file.

## read\_handle

    my $hash_ref = Config::Pg::ServiceFile->read_handle($io_handle);

Given an IO::Handle, this method returns a hashref of the contents of that
handle.

## read\_string

    my $hash_ref = Config::INI::Reader->read_string($string);

Given a string, this method returns a hashref of the contents of that string.

# AUTHOR

Paul Williams <kwakwa@cpan.org>

# COPYRIGHT

Copyright 2018- Paul Williams

# LICENSE

This library is free software; you can redistribute it and/or modify it under
the same terms as Perl itself.

# SEE ALSO

[Config::INI::Reader](https://metacpan.org/pod/Config::INI::Reader),
[Pg::ServiceFile](https://metacpan.org/pod/Pg::ServiceFile),
[https://www.postgresql.org/docs/current/static/libpq-pgservice.html](https://www.postgresql.org/docs/current/static/libpq-pgservice.html),
[https://github.com/postgres/postgres/blob/master/src/interfaces/libpq/fe-connect.c](https://github.com/postgres/postgres/blob/master/src/interfaces/libpq/fe-connect.c).
