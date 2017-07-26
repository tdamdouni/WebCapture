# 5 Regular Expressions Every Web Programmer Should Know

_Captured: 2015-12-11 at 10:02 from [web.archive.org](http://web.archive.org/web/20090318193321/http://immike.net/blog/2007/04/06/5-regular-expressions-every-web-programmer-should-know/)_

I'm going to assume you have a basic understanding of regular expressions at this point. If you're a regex n00b (or `/n0{2}b/`, as I like to call them), or if you need a quick refresher, check out my previous post on [the absolute bare minimum that every programmer should know about regular expressions](http://web.archive.org/web/20090318193321/http://immike.net/blog/2007/04/06/the-absolute-bare-minimum-every-programmer-should-know-about-regular-expressions/). You won't be disappointed.

So, without further adu, here are the five regular expressions that I have found the most useful for day-to-day web programming tasks.

### Matching a username

This one's quite easy, but it's really invaluable if you're trying to build a user registration system for a website. We typically want to limit usernames to a restricted set of characters in order to make development easier, and to keep malicious users from spoofing someone else's name (e.g. replacing a space with multiple spaces or a newline character, which are all displayed the same by a web browser).

Without regular expressions, this would be a tedious exercise that would involve splitting the string into it's component characters and examining each one individually. With regular expressions, it's a breeze. First, let's define what we want to accept, we'll keep it simple and limit the example to the following characters:

  1. Alphanumeric characters (letters and numbers)
  2. The underscore character (_)

We'll also want to enforce a 3 character minimum and a 16 character maximum length. Here's the regular expression that matches this fairly standard set of criteria:
    
    
    /[a-zA-Z0-9_]{3,16}/
    

If you're familiar with regular expressions you may have notice something missing at this point - don't worry, I'll get to it.

If you've read my [introductory to regular expressions](http://web.archive.org/web/20090318193321/http://immike.net/blog/2007/04/06/the-absolute-bare-minimum-every-programmer-should-know-about-regular-expressions/) you should already know how this regex works. First we're defining a character class that will match any letters (a through z, and A through Z) and any numbers (0 through 9), as well as the _ (_underscore_) character. Next comes an interval quantifier that tells the regex engine we'll only match sequences of between 3 and 16 characters. Because the quantifier follows a character class rather than a single character it attaches itself to the entire class, and will match every sequence between 3 and 16 characters so long as each character falls within our restricted character set.

So what's missing? As it stands our regex will match anywhere within a string. It won't just match 'mike_84′, it will also match any '%! mike_84&', which contains several characters we don't want. What we need are anchors, the ^ (_caret_) and $ (_dollar_) characters will anchor our regex to the beginning and end of the string, ensuring that the whole username meets our requirements and not just a portion of it.

So our revised regex will look like this:
    
    
    /^[a-zA-Z0-9_]{3,16}$/
    

Here's a quick PHP code snippet that shows how we can use this regex in production (we could just as easily use perl, java, ruby, or even javascript to do this validation).
    
    
    function validate_username( $username ) {
      if(preg_match('/^[a-zA-Z0-9_]{3,16}$/', $_GET['username'])) {
        return true;
      }
      return false;
    }
    

### Matching an XHTML/XML tag

Matching an XML or XHTML tag can be extremely useful if you're scraping a website for data, or trying to quickly extract information from an XML document. A simple regex to accomplish this sort of extraction follows this form (the word 'tag' should be replaced with whatever tag you are looking for):
    
    
    {<tag[^>]*>(.*?)</tag>}
    

The question mark following the star turns the start into a _lazy quantifier_. By default, quantifiers are _greedy_, meaning they'll consume as much of the input text as they can. Lazy quantifiers, by contrast, will match as little of the input text as they can. If we used a greedy quantifier in this case, our regex would not work as advertised on an input document like
    
    
    <tag>item 1</tag><tag>item 2</tag>
    

Instead of matching a single tag, a greedy quantifier would match up to the final closing tag in the input text.

Here's a simple PHP function to extract the contents of each matching XML or XHTML tag as an array:
    
    
    function get_tag( $tag, $xml ) {
      $tag = preg_quote($tag);
      preg_match_all('{<'.$tag.'[^>]*>(.*?)</'.$tag.'>.'}',
                       $xml,
                       $matches,
                       PREG_PATTERN_ORDER);
    
      return $matches[1];
    }
    

### Matching an XHTML/XML tag with a certain attribute value (e.g. class or tag)

This regex is very similar to the last example, except we only want tags with a certain attribute value. This comes in handy when you want to extract a tag with a particular class or ID value, for example. The regex is just slightly more complicated than our previous example (again, replace tag, attribute, and value with whatever you're looking for):
    
    
    {<tag[^>]*attribute\\s*=\\s*(["'])value\\\\1[^>]*>(.*?)</tag>}
    

We use a character class to allow either single or double quotes around our value. The portion of the regex following the value is called a _backreference_. It will be replaced with whatever is captured by the first set of parenthesis in the expression (either a single quote or double quote). That way we can be sure that the opening and closing quotes match.

Here's a PHP function that shows how you can extract information form an XHTML document with this regex. The function tags an attribute, value, input text, and an optional tag name as arguments. If no tag name is specified it will match any tag with the specified attribute and attribute value.
    
    
    function get_tag( $attr, $value, $xml, $tag=null ) {
      if( is_null($tag) )
        $tag = '\\w+';
      else
        $tag = preg_quote($tag);
    
      $attr = preg_quote($attr);
      $value = preg_quote($value);
    
      $tag_regex = "/<(".$tag.")[^>]*$attr\\s*=\\s*".
                    "(['\\"])$value\\\\2[^>]*>(.*?)<\\/\\\\1>/"
    
      preg_match_all($tag_regex,
                     $xml,
                     $matches,
                     PREG_PATTERN_ORDER);
    
      return $matches[3];
    }
    

### Matching and parsing an email address

This one comes courtesy of [Cal Henderson](http://web.archive.org/web/20090318193321/http://www.iamcal.com/), the programmer behind [Flickr](http://web.archive.org/web/20090318193321/http://www.flickr.com/) and author of [Building Scalable Web Sites](http://web.archive.org/web/20090318193321/http://www.amazon.com/exec/obidos/ASIN/0596102356) (a _great_ read). For more information check out [Cal's article on parsing email addresses](http://web.archive.org/web/20090318193321/http://www.iamcal.com/publish/articles/php/parsing_email/).

This one's such a behemoth that it's easier to digest when broken into it's component parts. Constructing a regex like this is a bit like describing a grammer in [Backus-Naur form](http://web.archive.org/web/20090318193321/http://en.wikipedia.org/wiki/Backus-Naur_form) (_BNF_), which is convenient because many of the things we're trying to match are already described using BNF in their specifications. This is the case for email addresses, which are described in [RFC 822](http://web.archive.org/web/20090318193321/http://www.faqs.org/rfcs/rfc822.html). Anyways, here's a PHP function that will check the validity of an e-mail address:
    
    
    function is_valid_email_address($email){
      $qtext = '[^\\x0d\\x22\\x5c\\x80-\\xff]';
      $dtext = '[^\\x0d\\x5b-\\x5d\\x80-\\xff]';
      $atom = '[^\\x00-\\x20\\x22\\x28\\x29\\x2c\\x2e\\x3a-\\x3c'.
                      '\\x3e\\x40\\x5b-\\x5d\\x7f-\\xff]+';
      $quoted_pair = '\\x5c[\\x00-\\x7f]';
      $domain_literal = "\\x5b($dtext|$quoted_pair)*\\x5d";
      $quoted_string = "\\x22($qtext|$quoted_pair)*\\x22";
      $domain_ref = $atom;
      $sub_domain = "($domain_ref|$domain_literal)";
      $word = "($atom|$quoted_string)";
      $domain = "$sub_domain(\\x2e$sub_domain)*";
      $local_part = "$word(\\x2e$word)*";
      $addr_spec = "$local_part\\x40$domain";
    
      return preg_match("!^$addr_spec$!", $email) ? 1 : 0;
    }
    

The '\x##' sequences are hexadecimal character references. It's just a fancy way of specifying a character using it's underlying code point (the numerical representation of a particular symbol). Otherwise this is a fairly straightforward, albeit incredibly complex regular expression. I'll refrain from any further analysis since it's been done [elsewhere](http://web.archive.org/web/20090318193321/http://www.iamcal.com/publish/articles/php/parsing_email/).

[Tim Fletcher](http://web.archive.org/web/20090318193321/http://tfletcher.com/) has ported Cal's original PHP function into [Ruby](http://web.archive.org/web/20090318193321/http://tfletcher.com/lib/rfc822.rb) and [Perl](http://web.archive.org/web/20090318193321/http://tfletcher.com/lib/rfc822.py), if that's what you're into..

### Matching a URL

Matching a URL is a lot like matching an e-mail address, except that you tend to do it in more controlled, and less critical situations where you can tolerate a few false positives. I use this regex frequently in projects when I need to automatically generate links when a URL is typed in a comment field, for example. Like the email regex, this one's a doozy, but it's pretty easy to understand.

I've taken advantage of the 'x' and 'i' _pattern modifiers_ for this regex. Pattern modifiers are tacked onto the end of a regex and change the way the regex engine interprets the expression. The 'x' modifier tells the engine to ignore whitespace, except when escaped or used inside of a character class. It also tells the engine to interpret any text following a '#' character outside of a character class as a comment (i.e. ignore it). The 'i' modifier makes the regex case insensitive. This can drastically simplify a complicated regex like this one when case doesn't matter. This regex is derived from one developed by Jeffrey Friedl in his book _[Mastering Regular Expressions](http://web.archive.org/web/20090318193321/http://www.amazon.com/gp/product/0596528124/ref=pd_cp_b_title/102-7486746-3142504?pf_rd_m=ATVPDKIKX0DER&pf_rd_s=center-41&pf_rd_r=1HKNXWMTVFF257YA2P0X&pf_rd_t=201&pf_rd_p=252362401&pf_rd_i=1565922573)_.
    
    
    {
      \\b
      # Match the leading part (proto://hostname, or just hostname)
      (
        # http://, or https:// leading part
        (https?)://[-\\w]+(\\.\\w[-\\w]*)+
      |
        # or, try to find a hostname with more specific sub-expression
        (?i: [a-z0-9] (?:[-a-z0-9]*[a-z0-9])? \\. )+ # sub domains
        # Now ending .com, etc. For these, require lowercase
        (?-i: com\\b
            | edu\\b
            | biz\\b
            | gov\\b
            | in(?:t|fo)\\b # .int or .info
            | mil\\b
            | net\\b
            | org\\b
            | [a-z][a-z]\\.[a-z][a-z]\\b # two-letter country code
        )
      )
    
      # Allow an optional port number
      ( : \\d+ )?
    
      # The rest of the URL is optional, and begins with /
      (
        /
        # The rest are heuristics for what seems to work well
        [^.!,?;"\\'<>()\[\]\{\}\s\x7F-\\xFF]*
        (
          [.!,?]+ [^.!,?;"\\'<>()\\[\\]\{\\}\s\\x7F-\\xFF]+
        )*
      )?
    }ix
    

The comments in this expression are fairly self explanatory, so I don't think it needs a whole lot of explanation. There are a few things to watch out for though. First, this regex will match some things that are not valid URLs. The regex assumes that any two-letter combination is a valid top-level domain (_TLD_), which is not the case. It also misses TLDs that were recently added to the IANA list like .travel, .name, and .museum. You can fix this by downloading the [latest IANA TLD list](http://web.archive.org/web/20090318193321/http://data.iana.org/TLD/tlds-alpha-by-domain.txt) and adding any missing TLDs in the list of alternatives mid-way through the expression.

That being said, this regex works great 99.9% of the time. Here's a quick PHP function that will parse a section of text, replacing any URLs it finds with links. I'm going to assume you've set the variable $url_regex to the the above pattern so I don't have to repeat it here.
    
    
    function auto_link( $text ) {
      $url_regex = ...
    
      return preg_replace( $url_regex,
                             '<a href="$0"^gt;$0=</a>',
                             $text );
    }
    

So that's it. If you think I left something off the list that deserves mention, or if you have any suggestions for improvements, post a comment and let me know.
