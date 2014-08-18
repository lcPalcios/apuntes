.. _reference-programacion-javascript-to_up_scroll:

############
Scroll Up To
############

**Fuentes**

* http://jsfiddle.net/5bNmH/1/

----

**Html**

Usa el glyphicon de Bootstrap

.. code-block:: html

    <diV class="go-top">
        <span class="glyphicon glyphicon glyphicon-chevron-up"></span>
    </diV>

**Javascript**

Requiere Jquery

.. code-block:: javascript

    $(document).ready(function() {
        // Show or hide the sticky footer button
        $(window).scroll(function() {
            if ($(this).scrollTop() > 200) {
                $('.go-top').fadeIn(200);
            } else {
                $('.go-top').fadeOut(200);
            }
        });

        // Animate the scroll to top
        $('.go-top').click(function(event) {
            event.preventDefault();

            $('html, body').animate({scrollTop: 0}, 300);
        })
    });

**CSS**

.. code-block:: css

    .go-top {
        position: fixed;
        bottom: 2em;
        right: 2em;
        text-decoration: none;
        color: white;
        background-color: rgba(0, 0, 0, 0.3);
        font-size: 12px;
        padding: 1em;
        display: none;
        cursor: pointer;
    }

    .go-top:hover {
        background-color: rgba(0, 0, 0, 0.6);
    }

