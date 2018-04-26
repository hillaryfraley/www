{# Set the `speakers` and `conf` variables before including this template #}

{% for talk in data %}

{% for speaker in talk.speakers %}
.. _speaker-{{ conf }}-{{ speaker.slug }}:
{% endfor %}

.. Comment to break up reference issues

.. raw:: html

    {% for speaker in talk.speakers %}
    <a name="speaker-{{ speaker.slug }}"></a>
    {% endfor %}
    <div class="row row-speaker">
      <div class="col-md-2 col-md-offset-1 col-sm-2 col-sm-offset-1">
        {% for speaker in talk.speakers %}
        <img class="speaker-image" src="/_static/img/speakers/{{ speaker.img_file }}" />
        {% endfor %}
      </div>
      <div class="col-md-8 col-sm-8">
        <h3>
          {% for speaker in talk.speakers %}
          {{ speaker.name|indent(10) }}
          <span class="speaker-details">
          {% if speaker.twitter %}
          <a href="https://twitter.com/{{ speaker.twitter }}">@{{ speaker.twitter }}</a>
          {% endif %}
          </span>
          {% endfor %}
        </h3>
        <h4>{{ talk.title }}</h4>
        {{ talk.abstract|indent(10) }}
        {% if talk.youtubeId %}<a href="https://www.youtube.com/watch?v={{ talk.youtubeId }}">Watch "{{ talk.title }}" on YouTube.</a>{% endif %}
      </div>
    </div>

{% endfor %}
