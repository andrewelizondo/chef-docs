.. The contents of this file are included in multiple topics.
.. This file should not be changed in a way that hinders its ability to appear in multiple documentation sets.


Use the ``Chef::Log`` class in an |ohai| plugin to define log entries that are created during a |chef client| run. The syntax for a log message is as follows:

.. code-block:: ruby

   Chef::Log.log_type('message')

where

* ``log_type`` can be ``.debug``, ``.info``, ``.warn``, ``.error``, or ``.fatal`` 
* ``'message'`` is the message that is logged.

For example:

.. code-block:: ruby

   Ohai.plugin do
     provides 'openstack'
   
     collect_data do
       if hint?('openstack') || hint?('hp')
         Ohai::Log.debug('ohai openstack')
         openstack Mash.new
         if can_metadata_connect?(EC2_METADATA_ADDR,80)
           Ohai::Log.debug('connecting to the OpenStack metadata service')
           self.fetch_metadata.each {|k, v| openstack[k] = v }
           case
           when hint?('hp')
             openstack['provider'] = 'hp'
           else
             openstack['provider'] = 'openstack'
           end
         else
           Ohai::Log.debug('unable to connect to the OpenStack metadata service')
         end
       else
         Ohai::Log.debug('NOT ohai openstack')
       end
     end 
   end
