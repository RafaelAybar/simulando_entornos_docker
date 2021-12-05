Para configurar fluentbit, podemos usar esta configuración genérica dentro del fichero fluent-bit.conf


```
[SERVICE]
	log_level debug

# The stdin plugin allows to retrieve valid JSON text messages over the standard input interface (stdin)
[INPUT]
	Name forward

# The Record Modifier Filter plugin allows to append fields or to exclude specific fields.
[FILTER]
	Name record_modifier
	Match *
# The stdout output plugin allows to print to the standard output the data received through the input plugin.
[OUTPUT]
	Name es
	Match **
	Host elasticsearch
	Port 9200
	Index monitoring

```
