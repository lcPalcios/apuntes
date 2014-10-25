.. _reference-programacion-python-django-generar_slug_automaticamente:

###############################
Generar un slug automaticamente
###############################

.. code-block:: python

    import re

    from django.db import models
    from django.core.urlresolvers import reverse


    class Noticia(models.Model):
        titulo = models.CharField(max_length=200)
        slug = models.CharField(max_length=200, blank=True, editable=False)

        def __str__(self):
            return self.titulo

        def get_absolute_url(self):
            return reverse('AQUI_EL_NAME_DE_URLS.PY', kwargs={'slug': self.slug})

        def save(self):
            self.slug = re.sub(r'[^\w\d]+', '-', self.titulo.lower())
            super(Noticia, self).save()
