---
layout: page
title: Sticky Header
permalink: sticky-header.html
---

La méthode officielle (depuis WordPress 6.2 sorti en 2023) est montrée dans ce tutoriel : 

[learn.wordpress.org/lesson/adding-a-sticky-header-or-banner/](https://learn.wordpress.org/lesson/adding-a-sticky-header-or-banner/)

- Dans chaque template, il faut créer un bloc "Groupe" qui entoure le bloc En-Tête.
- Sur ce block "Groupe", appliquer la Position "Sticky".

Cette méthode a un gros inconvénient: on est obligé de l'appliquer pour *chaque modèle* utilisé dans le site.

## Méthode alternative avec CSS

Une [autre méthode est présentée par Mike McAlister](https://olliewp.com/fixing-the-sticky-header-bug-in-the-wordpress-site-editor/):

- Appliquer la Position "Sticky" *à l'intérieur* du template "En-Tête".
- Ajouter au site un CSS personnalisé:

```css
header:has(>.is-position-sticky) {
	position: sticky;
	top: calc( 0px + var( --wp-admin--admin-bar--height, 0px ) );
	z-index: 100;
}
```

Avec cette méthode, il suffit de faire ce réglage à un endroit dans le template "En-Tête". L'effet sera appliqué sur l'ensemble du site.

## Ressources

- [Un article sur les questions UX](https://www.nngroup.com/articles/sticky-headers/) liées au Sticky header.
- Un ticket WordPress qui discute l'amélioration de la fonctionnalité sticky header: [Add support for Position setting to Template Parts for Sticky Headers](https://github.com/wordpress/gutenberg/issues/50617) 