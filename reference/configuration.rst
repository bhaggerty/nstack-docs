.. _configuration

Configuration
=============

In addition to receiving input at runtime, modules, sources, and sinks often need to be able to configured by a workflow author. To do this, we use brackets and pass in a list of named records: ::

   Sources.Postgres<Text> {
        pg_host = "localhost", 
        pg_port = "5432",
        pg_user = "user", 
        pg_password = "123456",
        pg_database = "db", 
        pg_query = "SELECT * FROM tbl;" 
    }

For sources and sinks, some parameters are mandatory, and some provide sensible defaults. This is documented in `Supported Integrations <supported_integrations>`_.

To pass configuration parameters to a module, we use the same syntax ::

  FirstLastName.full_name { first_name = "John" }

NStack passes in configuration parameters as a dictionary, ``args``, which is added to the base class of your module.
For instance, in Python you can access configuration parameters in the following manner:

.. code :: python 
  
  class Service(nstack.BaseService):
  
      def full_name(self, second_name):
        full_name = "{} {}".format(self.args.get("first_name", "Tux"), second_name)
        return full_name


