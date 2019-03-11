[![Cpan license](https://img.shields.io/cpan/l/SMS-Send-Mocean.svg)](https://metacpan.org/release/SMS-Send-Mocean)
[![Cpan version](https://img.shields.io/cpan/v/SMS-Send-Mocean.svg)](https://metacpan.org/release/SMS-Send-Mocean)

# NAME

SMS::Send::Mocean - SMS::Send driver to send messages via Mocean,
https://moceanapi.com/.

# SYNOPSIS

    use SMS::Send;

    my $gateway = SMS::Send->new(
        'Mocean',
        '_api_key' => 'foo',
        '_api_secret' => 'bar'
    );

    $gateway->send_sms(
        to => '+60123456789',
        ext => 'Hello',
        _from => 'foobar'
    );

# DESCRIPTION

SMS::Send::Mocean is a driver for [SMS::Send](https://metacpan.org/pod/SMS::Send) to send message via Mocean,
https://moceanapi.com/.

# DEVELOPMENT

Source repo at [https://github.com/kianmeng/send-sms-mocean](https://github.com/kianmeng/sms-send-mocean).

How to contribute? Follow through the [CONTRIBUTING.md](https://github.com/kianmeng/sms-send-mocean/blob/master/CONTRIBUTING.md) document to setup your development environment.

# METHODS

## new(\_api\_key, \_api\_secret)

Construct a new SMS::Send instance.

    my $gateway = SMS::Send->new(
        'Mocean',
        '_api_key' => 'foo',
        '_api_secret' => 'bar'
    );

### \_api\_key

Compulsory. The API access key used to make request through web service.

### \_api\_secret

Compulsory. The API secret key.

## send\_sms(to, text, \_from, \[%params\])

Send the SMS text to a mobile user.

    # Default parameters with XML response format if the '_resp_format' field
    # is not defined.
    $gateway->send_sms(
        to => '+60123456789',
        ext => 'Hello',
        _from => 'foobar',
    );

    # With JSON response format.
    $gateway->send_sms(
        to => '+60123456789',
        ext => 'Hello',
        _from => 'foobar',
        _resp_format => 'json',
    );

### to

Compulsory. The required field needed by SMS::Send. Only accept leading-plus
number in the format of "+99 XXX XXXX".

### text

Compulsory. The required field needed by SMS::Send. The content of the SMS
message. Depends on the language of the content, there is a limit of characters
that can be sent.

### \_from

Compulsory. The login username of the Mocean API portal.

### \[%params\]

Optional. Additional parameters that can be used when sending SMS. Check the
Mocean API documentation on the [available parameters](https://moceanapi.com/docs/#sms-api).
Due to the design constraints of [SMS::Send::Driver](https://metacpan.org/pod/SMS::Send::Driver), all parameters name must
start with underscore. For example, '\_resp\_format'. This driver will convert the
parameter name to equivalent format used by Mocean. In this case, '\_foo\_bar'
will be formatted as 'mocean-resp-format'.

    $gateway->send_sms(
        to => '+60123456789',
        ext => 'Hello',
        _from => 'foobar',
        _resp_format => 'json',
        _charset => 'utf-8',
    );

# COPYRIGHT AND LICENSE

This software is Copyright (c) 2019 Kian Meng, Ang.

This is free software, licensed under:

    The Artistic License 2.0 (GPL Compatible)

# AUTHOR

Kian Meng, Ang <kianmeng@users.noreply.github.com>

# SEE ALSO

[SMS::Driver](https://metacpan.org/pod/SMS::Driver)
