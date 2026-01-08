---
layout: default
title: Mes Réalisations
permalink: /projets/
---

<style>
    .project-card { transition: transform 0.3s ease; background: white; padding: 25px; border-radius: 12px; box-shadow: 0 5px 15px rgba(0,0,0,0.08); margin-bottom: 30px; }
    .project-card:hover { transform: translateY(-8px); box-shadow: 0 12px 24px rgba(0,0,0,0.15); }
    .btn-github { background-color: #333; color: white; border: none; margin-right: 10px; }
    .btn-site { background-color: #fed136; color: black; border: none; font-weight: bold; }
</style>

<section class="bg-light-gray" style="padding: 60px 0;">
    <div class="container">
        <div class="row">
            <div class="col-lg-12 text-center">
                <h2 class="section-heading">Mes Projets Détaillés</h2>
                <hr class="primary" style="max-width: 50px; border-width: 3px; border-color: #fed136;">
            </div>
        </div>

        <div class="row">
            {% for post in site.posts %}
            <div class="col-md-6">
                <div class="project-card">
                    <img src="{{ site.baseurl }}/img/{{ post.thumbnail }}" class="img-responsive" style="border-radius: 8px; margin-bottom: 20px;">
                    <h3>{{ post.title }}</h3>
                    <p class="text-muted" style="font-size: 0.9em; margin-bottom: 20px;">{{ post.description }}</p>
                    
                    <div class="project-links">
                        <a href="{{ post.project-url }}" target="_blank" class="btn btn-github">
                            <i class="fa fa-github"></i> Code Source
                        </a>
                        {% if post.live-url != "" %}
                        <a href="{{ post.live-url }}" target="_blank" class="btn btn-site">
                            Voir le Site
                        </a>
                        {% else %}
                        <button class="btn btn-default" disabled>Site bientôt en ligne</button>
                        {% endif %}
                    </div>
                </div>
            </div>
            {% endfor %}
        </div>
    </div>
</section>