Puppet server
=============

Puppet server set up

Requirements
------------

**node_terminus = ldap** requires *jruby-ldap*:
```bash
$ puppetserver gem install jruby-ldap
```
and the patch to
*/opt/puppetlabs/puppet/lib/ruby/gems/2.1.0/gems/jruby-ldap-0.0.2/lib/ldap/entry.rb*
or
*/opt/puppetlabs/server/data/puppetserver/jruby-gems/gems/jruby-ldap-0.0.2/lib/ldap/entry.rb*

```ruby
module LDAP

.....

  class Entry
.....
    def to_hash
       h = {}
       get_attributes.each { |a| h[a.to_sym] = self[a] }
       h[:dn] = [dn]
       h
    end
.....
```


Role Variables
--------------

Dependencies
------------

Example Playbook
----------------


License
-------

MIT

Author Information
------------------

Maxim Nazarenko <maxim.nazarenko@onix-systems.com>
