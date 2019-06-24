# tiny-ruby-tips

Ruby tips that fit in a tweet!

## The Tips

<!--
Hello, tip author! Here is some friendly advice:

When you add a tip, use this for the Discuss button:

    [![Discuss on Twitter](/assets/discuss.svg)](<TWEET_URL>)
-->

- [#1: Memoizing nil or false](#1-memoizing-nil-or-false)

### #1: Memoizing nil or false

When you want to memoize a calculation that can return `nil` or `false`, you can check whether the instance variable is `defined?`.

```ruby
def foo
  return @foo if defined? @foo

  @foo = calculate_foo
end
```

[![Discuss on Twitter](/assets/discuss.svg)](https://twitter.com/ReinH/status/1142131218286145536)
