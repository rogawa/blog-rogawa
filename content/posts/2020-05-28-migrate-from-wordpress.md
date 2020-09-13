---
author:
  name: "Rui Ogawa"
date: 2020-05-28
linktitle: Migrando do Wordpress para Hugo e hospedando nas Githubpages 
title: Migrando do Wordpress para Hugo e hospedando nas Githubpages
type:
- post
- posts
weight: 10
series:
- Hugo 101
aliases:
- /blog/migrate-from-wordpress/
---

## Eu realmente preciso de um blog dinâmico?
Eu me associei ao [Wordpress.com](https://www.wordpress.com) em janeiro de 2007, ano provável da criação do meu primeiro blog, em que eu escrevia principalmente sobre [Software Livre](https://pt.wikipedia.org/wiki/Software_livre).

Com o passar dos anos, percebi que gastava um tempo e recurso precioso com coisas que podiam ser feitas de forma muito mais simples e gratuita. Comecei a pesquisar sobre plataformas estáticas para blog e encontrei o [Hugo](https://gohugo.io/). Há uma vasta documentação sobre como instalar e usar. Com a questão da plataforma estava resolvida, faltava decidir onde eu iria hospedar. A resposta eu encontrei ali mesmo, vendo que era possível [hospedar o Hugo nas Github Pages](https://gohugo.io/hosting-and-deployment/hosting-on-github/). Eu não vou escrever aqui sobre os procedimentos de Instalação e configuração do Hugo, uso do Github e do Github Pages, pois basta seguir a documentação oficial e ser feliz.

Agora eu precisava migrar o conteúdo do Wordpress para o formato do Hugo. A forma mais rápida que encontrei de fazer isso foi usando o [WordPress to Hugo Exporter
](https://github.com/SchumacherFM/wordpress-to-hugo-exporter), um plugin para Wordpress. Ai foi só baixar todo o conteúdo em um pacote zip, descompactá-lo e ir colocando os posts no diretório `content/posts`. 


Tem uma dica [AQUI](https://www.elliotsachs.com/how-to-tell-hugo-to-open-links-in-new-tab/) para que um link abra sempre em uma nova aba ou janela. Crie um diretório `layouts/_default/_markup/render-link.html` e coloque o seguinte conteúdo nele.

    {{< highlight html >}}
    <a href="{{ .Destination | safeURL }}"{{ with .Title}} title="{{ . }}"{{ end }}{{ if strings.HasPrefix .Destination "http" }} target="_blank"{{ end }}>
    {{ .Text }}
    </a>
    {{< /highlight >}}


