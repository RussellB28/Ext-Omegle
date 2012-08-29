Ext::Omegle Module for Perl
============================================================
------------------------------------------------------------

## Table of Contents
1.   Description
2.   Developers
3.   Requirements
4.   How to install
5.   How to upgrade
6.   Help, Bugs, Suggestions

------------------------------------------------------------
## 1. DESCRIPTION

Ext::Omegle is a Perl interface for omegle.com which allows you to talk to strangers online.

## 2. DEVELOPERS

Ext::Omegle is currently maintained and developed by the following people:

+ Russell Bradford &lt;russell@rbradford.me&gt;

A previous and old version of this module made for Perl was also developed by:

+ Mischa Spiegelmock &lt;revmischa@cpan.org&gt;

## 3. REQUIREMENTS
Ext::Omegle Required Perl (5.10+) to be installed. If you use *nix most package managers have this as 'perl'.
If you're using OS X, this is already installed on your system. Lastly, if you're using Windows we suggest [Strawberry Perl](http://strawberryperl.com/).
Ext::Omegle also requires a few CPAN modules in order to correctly function, they are:

+ WWW::Mechanize
+ HTTP::Async
+ HTTP::Request::Common

## 4. HOW TO INSTALL

To install this module type the following:

   perl Makefile.PL
   make
   make test
   make install

## 5. HOW TO UPGRADE

There is currently no official method of upgrading.

## 6. Example Code

The Following Code is an example of how the module could be used:

  use Ext::Omegle;
  my $obot = Ext::Omegle->new(
                             on_connect    => \&connect_cb,
                             on_chat       => \&chat_cb,
			     on_recaptcha  => \&recaptcha_cb,
			     on_recaptcharejected  => \&recaptchareject_cb,
                             on_disconnect => \&disconnect_cb,
		             on_typing => \&typing_cb,
			     on_stoptyping => \&stoptyping_cb,
                             );

  $obot->start;
  while ($obot->get_next_event) { 1; }
  exit;

  sub connect_cb {
    my ($om) = @_;
    print "[OMEGLE] Connected\n";
    $om->say('Hello!');
  }

  sub chat_cb {
    my ($om, $what) = @_;
    print "[OMEGLE] $what\n";
  }

  sub recaptcha_cb {
    my ($om, $what) = @_;
    print "[OMEGLE] Captcha Recieved (Challenge: $what)\n";
  }

  sub recaptchareject_cb {
    my ($om) = @_;
    print "[OMEGLE] Catpcha Rejected, Disconnecting.\n";
    $om->disconnect;
  }

  sub disconnect_cb {
    my ($om) = @_;
    print "[OMEGLE] Disconnected.\n";
  }

  sub typing_cb {
    my ($om, $what) = @_;
    print "[OMEGLE] Stranger is typing...\n";
  }

  sub stoptyping_cb {
    my ($om, $what) = @_;
    print "[OMEGLE] Stranger has stopped typing.\n";
  }

## 7. HELP, BUGS, SUGGESTIONS

For help with Ext::Omegle, you can ask on my IRC chatroom at irc.evosurge.net
&#35;russell.

To report a bug, please visit our IRC channel.
Thanks for contributing by reporting issues!

