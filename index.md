---
layout: home
title: "SQLSaturday"
---
Welcome to SQLSaturday, the data platform and SQL Server community franchise for technical events. We have a list of <a href="#events">upcoming events</a> below as well as <a href="#reserved">reserved dates</a>. There are also <a href="#other">other events</a> from different sources that are of interest to the data professional.

If you want to know more about events from an organizer, speaker, sponsor, or attendee standpoint, sign up for our [mailing list](http://eepurl.com/hwVBKn)

## <a name="events"></a>Events

These are the SQLSaturday events that are currently scheduled. If you would like to organize or schedule an event, please visit our [running a new event](http://beta.sqlsaturday.com/newevent/) page.

<table cellspacing=0 class="table table-hover table-borderless table-sortable mt-3" width="100%">
  <thead>
        <tr>
          <th scope="col"></th>
          <th scope="col">Event Name</th>
          <th scope="col">Date</th>
        </tr>
      </thead>
      <tbody>
  {% assign TodayDate = site.time | date: '%s' %}
  {% assign future = 0 %}
  {% for post in site.posts reversed %}
    {% assign EventDate = post.date | date: '%s' %}
    {% if post.testevent != 1 %}
      {% if EventDate > TodayDate %}
        {% assign future = 1 %}
        <tr>
          <td><img src="{{ post.thumb }}"></td>
          <td><a href="{{ post.url | absolute_url }}">{{ post.title }}</a>
          </td>
          <td>{% if post.postponed == 1 %}
                <b>Postponed</b>
              {% else %}  {{post.date | date_to_long_string }}
              {% endif %}
          </td>
        </tr>
      {% endif %}
   {% endif %}
  {% endfor %}
  {% if future == 0 %}
    <tr>
    <td><img src="/assets/img/logos/Just_icon_Color_small.png"></td>
      <td>No future events scheduled at this time
      </td>
      <td>&nbsp;</td>
    </tr>
  {% endif %}
  </tbody>
</table>

## <a name="reserved"></a>Reserved Dates

The following dates are tentative for these cities, but they have asked to reserve the date:
- December 9, 2023 - Lima, Peru 
- October 7, 2023 - Toronto, Canada


You can see completed events on the [Past Events](past) page.

## <a name="other"></a>Other Events

Here are some other events that you might find interesting as a data professional:

<table cellspacing=0 class="table table-hover table-borderless table-sortable mt-3" width="100%">
  <thead>
        <tr>
          <th scope="col"></th>
          <th scope="col">Event Name</th>
          <th scope="col">Date</th>
        </tr>
  </thead>
  <tbody>
        {% for block in site.data.otherevents.events %}
        {% assign thumbnail = block.thumb %}
        <tr>
          <td>
            {% if thumbnail %}
              <img src="{{ block.thumb }}">
            {% else %}
               &nbsp;
            {% endif %}
          </td>
          <th scope="col"><a href="{{ block.url }}">{{ block.title }}</a></th>
          <th scope="col">{{ block.date }}</th>
        </tr>
        {% endfor %}
  </tbody>
