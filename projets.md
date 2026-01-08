---
layout: default
title: Mes Réalisations
permalink: /projets/
---

<style>
    .projects-section { padding: 80px 0; background-color: #f4f7f6; }

    .project-card { 
        background: #ffffff; border-radius: 20px; overflow: hidden;
        display: flex; flex-direction: column; height: 100%;
        transition: all 0.4s cubic-bezier(0.165, 0.84, 0.44, 1); 
        box-shadow: 0 10px 30px rgba(0, 0, 0, 0.05);
        border: 1px solid rgba(0,0,0,0.08);
    }
    
    .project-card:hover { 
        transform: translateY(-12px);
        box-shadow: 0 25px 50px rgba(0, 0, 0, 0.15);
    }

    .img-wrapper { width: 100%; height: 200px; overflow: hidden; background-color: #eee; }
    .img-uniform { 
        width: 100%; height: 100%; 
        object-fit: cover; 
        object-position: center;
        transition: transform 0.6s cubic-bezier(0.165, 0.84, 0.44, 1);
    }
    
    .project-card:hover .img-uniform { transform: scale(1.15); }

    .content-area { padding: 30px; flex-grow: 1; display: flex; flex-direction: column; }
    
    .project-title { font-size: 1.6rem; font-weight: 900; margin-bottom: 15px; color: #1a1a1a; letter-spacing: -0.5px; }
    
    /* --- DESCRIPTION UNIFORME ET PLUS GROSSE --- */
    .project-desc { 
        font-size: 1.1rem; 
        color: #333; 
        font-weight: 600; 
        line-height: 1.6;
        margin-bottom: 25px;
        /* Force l'affichage sur exactement 3 lignes */
        display: -webkit-box;
        -webkit-line-clamp: 3;
        -webkit-box-orient: vertical;  
        overflow: hidden;
        height: 5.2em; /* Assure que toutes les boxes font la même taille */
    }

    .tech-stack { display: flex; gap: 12px; margin-bottom: 25px; flex-wrap: wrap; }
    
    .tech-badge {
        display: flex; align-items: center; justify-content: center;
        width: 45px; height: 45px; background: #f8f9fa; border-radius: 12px;
        border: 1px solid #e9ecef; transition: all 0.3s ease;
    }
    
    .tech-badge i { font-size: 1.8rem; display: flex; align-items: center; justify-content: center; }
    .project-card:hover .tech-badge { transform: scale(1.1); border-color: #fed136; }
    
    .fa-html5 { color: #E34F26; }
    .fa-css3-alt { color: #1572B6; }
    .fa-js { color: #F7DF1E; background: #000; padding: 2px; border-radius: 4px; }

    .button-group { display: flex; gap: 15px; margin-top: auto; }
    
    /* --- BOUTONS PLUS GROS --- */
    .btn-custom {
        padding: 15px 20px; 
        border-radius: 14px; 
        font-size: 1.05rem;
        font-weight: 800; 
        text-decoration: none !important; 
        transition: all 0.3s;
        display: inline-flex; 
        align-items: center; 
        gap: 10px; 
        flex: 1; 
        justify-content: center;
    }
    .btn-github { background: #000; color: #fff !important; }
    .btn-live { background: #fed136; color: #000 !important; }
    .btn-custom:hover { transform: translateY(-3px); filter: brightness(1.1); }
</style>

<section class="projects-section">
    <div class="container">
        <div class="row">
            <div class="col-lg-12 text-center" style="margin-bottom: 60px;">
                <h2 class="section-heading" style="font-weight: 900; font-size: 3rem;">Mes Réalisations</h2>
                <hr style="width: 60px; border: 3px solid #fed136; margin: 20px auto;">
            </div>
        </div>

        <div class="row">
            {% for post in site.posts %}
            <div class="col-md-4 col-sm-6" style="margin-bottom: 40px;">
                <div class="project-card">
                    <div class="img-wrapper">
                        <img src="{{ site.baseurl }}/img/{{ post.thumbnail }}" class="img-uniform">
                    </div>
                    <div class="content-area">
                        <div class="tech-stack">
                            {% assign techs = post.technologies | split: ", " %}
                            {% for tech in techs %}
                            <div class="tech-badge">
                                <i class="fa-brands fa-{{ tech }}" title="{{ tech | upcase }}"></i>
                            </div>
                            {% endfor %}
                        </div>
                        <h3 class="project-title">{{ post.title }}</h3>
                        <p class="project-desc">{{ post.description }}</p>
                        
                        <div class="button-group">
                            <a href="{{ post.project-url }}" target="_blank" class="btn-custom btn-github">
                                <i class="fa-brands fa-github fa-lg"></i> Code
                            </a>
                            {% if post.live-url != "" %}
                            <a href="{{ post.live-url }}" target="_blank" class="btn-custom btn-live">
                                <i class="fa-solid fa-arrow-up-right-from-square"></i> Live
                            </a>
                            {% endif %}
                        </div>
                    </div>
                </div>
            </div>
            {% endfor %}
        </div>
    </div>
</section>