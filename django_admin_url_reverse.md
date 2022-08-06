#python #django #djang_admin

[source](https://stackoverflow.com/a/2930241)
[Documentation](https://docs.djangoproject.com/en/dev/ref/contrib/admin/#reversing-admin-urls)

### Quick Example
`polls` -- app_label
`choice` -- model_name
```
{% url 'admin:index' %}
{% url 'admin:login' %}
{% url 'admin:logout' %}
{% url 'admin:password_change' %}
{% url 'admin:password_change_done' %}
{% url 'admin:jsi18n' %}
{% url 'admin:app_list' app_label %}
{% url 'admin:view_on_site' content_type_id object_id %}

{% url 'admin:auth_user_password_change' user_id %}

{% url 'admin:polls_choice_changelist' %}
{% url 'admin:polls_choice_add' %}
{% url 'admin:polls_choice_change' choice.id %}
{% url 'admin:polls_choice_history' choice.id %}
{% url 'admin:polls_choice_delete' choice.id %}
```
