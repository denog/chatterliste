---
layout: liste
---
<table>
  <thead>
    <tr>
      <th>Nick</th>
      <th>Name</th>
      <th>NIC-Handle</th>
      <th>ASN</th>
      <th>Organisation</th>
    </tr>
  </thead>
  <tbody>
  {% for entry in site.data.chatterliste %}
    <tr>
      <td>{{ entry.Nick }}</td>
      <td>{{ entry.Name }}</td>
      <td>
        {% if entry["NIC Handle"] %}
        <a href="http://apps.db.ripe.net/search/query.html?searchtext={{ entry["NIC Handle"] }}&flags=r&types=PERSON">{{ entry["NIC Handle"] }}</a>
        {% endif %}
      </td>
      <td>
        {% if entry.ASN %}{% for asn in entry.ASN %}
          <a href="http://apps.db.ripe.net/search/query.html?searchtext=AS{{ asn }}&flags=r&types=AUT_NUM">{{ asn }}</a><br>
        {% endfor %}{% endif %}
      </td>
      <td>
        {% if entry.Organisation %}{% for org in entry.Organisation %}
          {% if org.url %}<a href="{{ org.url }}">{% endif %}
          {{ org.name }}
          {% if org.url %}</a>{% endif %}
          <br>
        {% endfor %}{% endif %}
      </td>
    </tr>
  {% endfor %}
  </tbody>
</table>
