{{title}}
{% if subtitle %}{{subtitle}}
{% endif %}
Inbetween these email updates, you should be able to find our latest status at:
https://docs.google.com/presentation/d/1nupBVPwzWeUP6n-vJh5YEhYoHjecCkzFXQvt9V0GG88/edit

---

# OKR Summary
{% for objective in objectives | sort %}
{{objective}}{% for key, epic in epics.items() if epic and key in objectives[objective] %}
  {{ epic.raw['fields']['summary'].split('\n')[0] }} - {{ server }}/browse/{{ key }} - {{epic.percent_complete}}%{% endfor %}
{% endfor %}
---

{% for objective in objectives | sort %}# {{ objective }}
{% for key, epic in epics.items() if epic and key in objectives[objective] %}
{{ epic.raw['fields']['summary'].split('\n')[0].strip() }} - {{ server }}/browse/{{ key }}

- Progress:  {{epic.percent_complete}}%{% if epic.target_date %}
- Target: {{ epic.target_date}}{% endif %}{% if epic.mvp_status %}
- Status: {{ epic.mvp_status['value']}}{% endif %}{% if epic.status_update %}
- Update: (*{{epic.status_update.updated.split('T')[0]}}*) {{epic.status_update.cleaned}}{% if attribution %} — {{epic.status_update.author}}{% endif %}{% endif %}

---
{% endfor %}
{% endfor %}
# Thank you

For any questions, feel free to reach out to:

- Mike Bonnet <mikeb@redhat.com> (Product Owner)
- Lui Carvalho <lui@redhat.com> (Team Lead)

.. or, you can respond on list, or join to chat in #pnt-devops-dev.

Feedback on the format of this email is appreciated.  Too much detail?  Not enough?  Let us know.
