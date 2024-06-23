<template>
  <Layout>
    <div class="content">

      <section class="business-card">
  <div class="card">
    <img src="https://bastian.cazaux.nc/cv/logo.png" alt="Image de profil" class="profile-pic" />
    <h4>NEWCAL DEVMAN</h4>
    <p>Développeur Front-end Galactique</p>
    <p>Email: NEWCAL.DEVMAN@universe.com</p>
    <p>Téléphone: +687 68 76 87</p>
    <p>Adresse: Station Spatiale Internationale, Orbite Terrestre</p>
    <p>“Connu dans le multivers comme NEWCAL DEVMAN, je sauve des projets web avec ma force de code et mes pouvoirs de débogage laser.”</p>
    
    <!-- Lien vers le CV -->
    <br><a href="https://bastian.cazaux.nc/cv/" target="_blank" rel="noopener" class="card-link">Voir mon CV</a><br>

    <!-- Ajout des réseaux sociaux -->
    <div class="social-links">
      <a href="https://twitter.com" target="_blank" rel="noopener">
        <i class="fab fa-twitter"></i>
      </a>
      <a href="https://facebook.com" target="_blank" rel="noopener">
        <i class="fab fa-facebook-f"></i>
      </a>
      <a href="https://instagram.com" target="_blank" rel="noopener">
        <i class="fab fa-instagram"></i>
      </a>
    </div>
  </div>
</section>



      <br><br>

      <g-image alt="Exemple d'image" src="~/favicon.png" width="135" class="logo" />

      <h1>Développement Front</h1>
      <h2>Jamstack & SSR</h2>

      <section>
        <h3>Jamstack</h3>
        <p>
          Jamstack pour “Javascript - API - Markup” : toutes les pages dynamiques d’un site sont “pré-rendu” au moment de la compilation afin que l’ensemble du site ne fonctionne qu’avec des fichiers statiques.
          Toutes les opérations nécessitant l’usage d’un serveur (Envoi de formulaires, récupération de données, ...) doivent être exécutées au moyen d’une API hébergée sur un serveur distant.
          L’avantage étant qu’on peut ensuite héberger le projet sur n’importe quel serveur supportant des fichiers statiques et notamment cloud comme AWS S3 ou Netlify dont le coût est inférieur à un serveur classique avec base de données.
        </p>
      </section>

      <section>
        <h3>Gatsby</h3>
        <p>
          Un des framework Jamstack les plus intéressant à utiliser dans l’éco-système de React est Gatsby.
          Créé en 2015 par Kyle Mathews, Gatsby est désormais devenu en mai 2018 une start-up en effectuant une levée de fond initiale de 3,8 millions de dollars. Gatsby a été depuis racheté par Netlify.
        </p>
        <p>
          Gatsby dispose d’une forte communauté avec de nombreux plug-ins et starters.
          Gatsby est un “générateur de sites statique”, chacune des “pages” javascript de votre projet va être compilée en un fichier HTML unique déployable sur un serveur. On parle alors de SSR pour Server Side Rendering.
        </p>
        <p>
          Gatsby.js consomme également les données en les structurant dans un nœud final uniforme et central avec GraphQL. Le développeur qui travaille avec un site Gatsby écrit du code avec React et requête ses données avec GraphQL.
        </p>
        <p>
          Un premier projet avec le Gatsby Hello World
        </p>
        <p>
          On va d’abord installer le Gastby CLI (command line interface) qui va fournir toutes les méthodes pratiques pour utiliser Gatsby :
        </p>
        <pre><code>npm install -g gatsby-cli</code></pre>
        <p>
          Si vous avez besoin d’un peu d’aide : <code>gatsby — help</code></p>
        <p>
          Commençons par créer notre projet, pour faire simple on va utiliser le “starter” de gatsby qui n’est rien d’autre qu’un boilerplate intégrant react, react-dom, gatsby et prettier, le tout configuré correctement.
        </p>
        <p>
          Note : télécharger d’autres starters pour vous inspirez si nécessaire.
        </p>
        <pre><code>gatsby new hello-world https://github.com/gatsbyjs/gatsby-starter-hello-world</code></pre>
        <p>
          Déplacez vous (depuis votre console) dans le dossier du projet et lancez le serveur :
        </p>
        <pre><code>cd hello-world<br>gatsby develop</code></pre>
        <p>
          Utilisez maintenant la commande <code>gatsby build</code> pour créer vos fichiers statiques.
        </p>
        <p>
          Les fichiers de votre site sont désormais dans le répertoire public. Pour tester ces fichiers, utilisez <code>gatsby serve</code>
        </p>
        <p>
          Votre build contient uniquement des fichiers statiques… Pratique pour le SEO et le déploiement !
        </p>
        <p>
          Ajoutons maintenant une page à notre projet.
        </p>
        <p>
          Créez un fichier page-2.js dans le répertoire pages et insérez le code suivant :
        </p>
        <pre><code>import React from "react"<br>//module Link de gatsby pour les liens entre les pages<br>import { Link } from "gatsby"<br><br>export default function Page2() {<br>  return (<br>    &lt;div&gt;<br>      &lt;h1&gt;Page 2&lt;/h1&gt;<br>      &lt;Link to="/"&gt;Accueil&lt;/Link&gt;<br>    &lt;/div&gt;<br>  );<br>}</code></pre>
      </section>

      <section>
        <h3>Gridsome : Gatsby “version Vue”</h3>
        <p>
          Gridsome est l’adaptation de Gatsby avec Vue.js. Il fonctionne exactement sur le même principe mais avec une syntaxe adaptée.
        </p>
        <p>
          Tester un projet avec Gridsome
        </p>
        <p>
          Installer le Gridsome CLI (command line interface) :
        </p>
        <pre><code>npm install --global @gridsome/cli</code></pre>
        <p>
          Créez ensuite votre projet : <code>gridsome create mon-projet</code>
        </p>
        <p>
          Testez ensuite avec cette commande sur le serveur local <code>http://localhost:8080</code> :
        </p>
        <pre><code>gridsome develop</code></pre>
        <p>
          Composition d’un projet Gridsome
        </p>
        <ul>
          <li><code>gridsome.config.js</code> : la configuration de votre projet (plugins, etc.).</li>
          <li><code>gridsome.server.js</code> : fichier permettant l’ajout d’actions au moment de la compilation serveur.</li>
          <li><code>node_modules</code> : vos dépendances NPM.</li>
          <li><code>src/</code> : vos sources</li>
          <li><code>components/</code> : composants génériques</li>
          <li><code>layouts/</code> : fichier(s) de “ mise en page” globale</li>
          <li><code>pages/</code> : vos pages, chaque fichier présent ici créera une “route” à votre application.</li>
          <li><code>templates</code> : fichiers de templates pour des pages dynamiques.</li>
          <li><code>main.js</code> : le point d’entrée de votre application</li>
          <li><code>static</code> : fichiers statiques (images, etc.)</li>
        </ul>
        <p>
          “Build” du projet
        </p>
        <p>
          Pour ajouter une page, vous allez ensuite ajouter un fichier .vue dans <code>src/pages</code>
        </p>
        <p>
          Pour compiler votre projet, utilisez <code>gridsome build</code>.
        </p>
        <p>
          Vos fichiers sont ensuite disponibles dans le répertoire <code>dist</code>.
        </p>
      </section>
    </div>
  </Layout>
</template>

<script>
import Layout from '~/layouts/Default.vue';

export default {
  components: {
    Layout
  },
  metaInfo: {
    title: 'Développement Front - Jamstack & SSR',
    meta: [
      {
        name: 'description',
        content: 'Une page d\'information sur le développement front avec Jamstack et SSR.'
      },
      {
        name: 'keywords',
        content: 'Jamstack, SSR, Gatsby, Gridsome, Netlify'
      }
    ]
  }
}
</script>

<style scoped>
.content {
  max-width: 800px;
  margin: 0 auto;
  padding: 2rem;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

h1, h2, h3 {
  text-align: center;
}

footer {
  margin-top: 2rem;
  text-align: center;
}

.social-links {
  margin-top: 1rem;
  text-align: center;
  color: #fca311;
}

.social-links a {
  display: inline-block;
  margin: 0 10px;
  font-size: 1.5rem;
  color: inherit;
}

.social-links i {
  margin: 0 10px;
  font-size: 1.5rem;
}

.business-card {
  text-align: center;
  margin-top: 2rem;
}

.business-card .card {
  display: inline-block;
  padding: 1rem;
  border: 1px solid #ddd;
  border-radius: 8px;
  background-color: #f9f9f9;
  box-shadow: 0 2px 4px rgba(0, 0, 0, 0.1);
  background-color: #14213d;
  color: #2c3e50;
  max-width: 400px; /* Ajustez la largeur selon vos besoins */
  margin: 0 auto;
}

.business-card .profile-pic {
  border-radius: 50%;
  margin-bottom: 1rem;
}

.business-card h4 {
  margin: 0;
  font-size: 1.5rem;
  font-weight: bold;
  color: #fca311;
}

.business-card p {
  color: #ffffff;
  margin-bottom: 0.5rem;
}

.profile-pic {
  width: 300px; 
  height: auto;
  border-radius: 50%;
  margin-bottom: 1rem;
}

.card-link {
  display: block;
  text-decoration: none;
  background-color: #fca311;
  color: #14213d;
  font-weight: bold;
  padding: 10px 20px;
  border-radius: 5px;
  margin-top: 1rem;
  transition: background-color 0.3s ease;
}

.card-link:hover {
  background-color: #e5ac00;
}

.card-link:active {
  background-color: #d49900;
}
</style>
