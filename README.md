# tiny-ruby-tips

Ruby tips that fit in a tweet!

## The Tips

<!--
Hello, tip author! Here is some friendly advice:

When you add a tip, use this for the Discuss button:

    [![Discuss on Twitter](/assets/discuss.svg)](<TWEET_URL>)
-->

- [#1: Memoizing nil or false](#1-memoizing-nil-or-false)
- [#2: Hide / Show your cursor](#2-hide-and-show-your-cursor)
- [#3: Dealing with annoying namespacing](#3-dealing-with-annoying-namespacing)

### #1: Memoizing nil or false

When you want to memoize a calculation that can return `nil` or `false`, you can check whether the instance variable is `defined?`.

```ruby
def foo
  return @foo if defined? @foo

  @foo = calculate_foo
end
```

[![Discuss on Twitter](/assets/discuss.svg)](https://twitter.com/ReinH/status/1142131218286145536)


### #2: Hide and show your cursor

As a maker of excellent life decisions, you may one day discover you've lost your cursor.
It happens. Just remember `\e[?25h`. The `\e[` escapes terminal instructions,
`?number` is… IDK, probably a register address or smth.
And `h` is for high/on ( `l` for low/off)

![example](/assets/2-cursor.gif)

[![Discuss on Twitter](/assets/discuss.svg)](https://twitter.com/josh_cheek/status/1143057375076769792)


### #3: Dealing with annoying namespacing

You can deal with painful namespacing by opening the most convenient lexical scope
or by saving the namespace into a more convenient reference.

```ruby
require 'curb'
require 'elasticsearch/transport'
require 'elasticsearch/transport/transport/http/curb'

# Option 1: open up the most convenient lexical scope
# (modules and classes return the last expression evaluated in their body)
client = module Elasticsearch::Transport
  Client.new(
    transport: Transport::HTTP::Curb.new(hosts: [{host: 'localhost', port: 9200}])
  )
end

# Option 2: store a convenient reference to their namespace
# (here I use a local var, but if I'm in a class I'd prob save it into a constant)
es = Elasticsearch::Transport
client = es::Client.new(
  transport: es::Transport::HTTP::Curb.new(hosts: [{host: 'localhost', port: 9200}])
)
```

[![Discuss on Twitter](/assets/discuss.svg)](https://twitter.com/josh_cheek/status/1171183908366495746)
