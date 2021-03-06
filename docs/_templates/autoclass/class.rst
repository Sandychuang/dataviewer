{% if '__init__' in methods %}
{{ methods.remove('__init__') }}
{% endif %}

.. code-block:: python

   >>> from {{ module }} import {{ name }}

{{ docstring }}

{% block attributes_summary %}
{% if attributes %}

.. rubric:: Attributes Summary

.. autosummary::
{% for item in attributes %}
   ~{{ name }}.{{ item }}
{%- endfor %}

{% endif %}
{% endblock %}

{% block methods_summary %}
{% if methods %}

.. rubric:: Methods Summary

.. autosummary::
{% for item in methods %}
   ~{{ name }}.{{ item }}
{%- endfor %}

{% endif %}
{% endblock %}

{% block attributes_documentation %}
{% if attributes %}

.. rubric:: Attributes Documentation

{% for item in attributes %}
.. autoattribute:: {{ item }}
{%- endfor %}

{% endif %}
{% endblock %}

{% block methods_documentation %}
{% if methods %}

.. rubric:: Methods Documentation

{% for item in methods %}
.. automethod:: {{ item }}
{%- endfor %}

{% endif %}
{% endblock %}
