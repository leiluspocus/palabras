---
title: Look for a word in a group of div using only jQuery
date: "2016-03-22T18:44:23+00:00"
draft: false
template: post
slug: /en/look-for-a-word-group-divs/
category: Snippets
tags:
  - javascript
  - jquery
---
For an old project, I had to implement a search tool in a static page. No option for me to use any server side language, I had to implement that search tool using Javascript / jQuery.

The following function's purpose is to :

* Search amongst a group of divs that have the class qa-faqs if a word is present in the content
* Exclude stop-words in french and in english from the query entered by the user 
* List of words to exclude is in the var words\_to\_exclude
* Order the divs by data-relevance (times the searched word appears in each div)

Please note that the following function uses the awesome plugin [jQuery.highlight](http://bartaz.github.io/sandbox.js/jquery.highlight.html)

```javascript
jQuery.extend({
    highlight: function (node, re, nodeName, className) {
        if (node.nodeType === 3) {
            var match = node.data.match(re);
            if (match) {
                var highlight = document.createElement(nodeName || 'span');
                highlight.className = className || 'highlight';
                var wordNode = node.splitText(match.index);
                wordNode.splitText(match[0].length);
                var wordClone = wordNode.cloneNode(true);
                highlight.appendChild(wordClone);
                wordNode.parentNode.replaceChild(highlight, wordNode);
                return 1; //skip added node in parent
            }
        } else if ((node.nodeType === 1 && node.childNodes) && // only element nodes that have children
                !/(script|style)/i.test(node.tagName) && // ignore script and style nodes
                !(node.tagName === nodeName.toUpperCase() && node.className === className)) { // skip if already highlighted
            for (var i = 0; i &lt; node.childNodes.length; i++) {
                i += jQuery.highlight(node.childNodes[i], re, nodeName, className);
            }
        }
        return 0;
    }
});

jQuery.fn.unhighlight = function (options) {
    var settings = { className: 'highlight', element: 'span' };
    jQuery.extend(settings, options);

    return this.find(settings.element + "." + settings.className).each(function () {
        var parent = this.parentNode;
        parent.replaceChild(this.firstChild, this);
        parent.normalize();
    }).end();
};

jQuery.fn.highlight = function (words, options) {
    var settings = { className: 'highlight', element: 'span', caseSensitive: false, wordsOnly: false };
    jQuery.extend(settings, options);
    
    if (words.constructor === String) {
        words = [words];
    }
    words = jQuery.grep(words, function(word, i){
      return word != '';
    });
    words = jQuery.map(words, function(word, i) {
      return word.replace(/[-[\]{}()*+?.,\\^$|#\s]/g, "\\$&");
    });
    if (words.length == 0) { return this; };

    var flag = settings.caseSensitive ? "" : "i";
    var pattern = "(" + words.join("|") + ")";
    if (settings.wordsOnly) {
        pattern = "\\b" + pattern + "\\b";
    }
    var re = new RegExp(pattern, flag);
    
    return this.each(function () {
        jQuery.highlight(this, re, settings.element, settings.className);
    });
};


jQuery(document).ready(function($) {
  
  $("div[id^=qa-faq]").each(function () {
    var num = this.id.match(/qa-faq(\d+)/)[1];
    var faqContainer = $('.qa-faqs');
    var faq = $('#qa-faq' + num);
    
    if ( faqContainer.is('.collapsible') ) {

      faq.find('.qa-faq-anchor').bind("click", function() {
        if ( faqContainer.is('.accordion') ) {
          $('.qa-faq-answer').not('#qa-faq' + num + ' .qa-faq-answer').hide();
        }
        if ( faqContainer.is('.animation-fade') ) {
          faq.find('.qa-faq-answer').fadeToggle();
        } else if ( faqContainer.is('.animation-slide') ) {
          faq.find('.qa-faq-answer').slideToggle();
        } else  /* no animation */ {
          faq.find('.qa-faq-answer').toggle();
        }

        return false;
      });
    
      $('.expand-all.expand').bind("click", function() {
        $('.expand-all.expand').hide();
        $('.expand-all.collapse').show();
        if ( faqContainer.is('.animation-fade') ) {
          $('.qa-faq-answer').fadeIn(400);
        } else if ( faqContainer.is('.animation-slide') ) {
          $('.qa-faq-answer').slideDown();
        } else  /* no animation */ {
          $('.qa-faq-answer').show();
        }	
      });

      $('.expand-all.collapse').bind("click", function() {
        $('.expand-all.collapse').hide();
        $('.expand-all.expand').show();
        if ( faqContainer.is('.animation-fade') ) {
          $('.qa-faq-answer').fadeOut(400);
        } else if ( faqContainer.is('.animation-slide') ) {
          $('.qa-faq-answer').slideUp();
        } else  /* no animation */ {
          $('.qa-faq-answer').hide();
        }	
      });
      
    }
  });

  $('.qasubmission').bind("click", function() {
    $('#postbox').fadeToggle();
  });
  
  $('#qaplus_searchform').submit(function() { 
    query = $(this).find('.qaplus_search').val();
    jQuery('.no-results-found').hide();
    search(query); 
    return false;
  });

  function search(query) { 
    var words_to_exclude = 'a,able,about,across,after,all,almost,also,am,among,an,and,any,are,as,at,be,because,been,but,by,can,cannot,could,dear,did,do,does,either,else,ever,every,for,from,get,got,had,has,have,he,her,hers,him,his,how,however,i,if,in,into,is,it,its,just,least,let,like,likely,may,me,might,most,must,my,neither,no,nor,not,of,off,often,on,only,or,other,our,own,rather,said,say,says,she,should,since,so,some,than,that,the,their,them,then,there,these,they,this,tis,to,too,twas,us,wants,was,we,were,what,when,where,which,while,who,whom,why,will,with,would,yet,you,your,alors,au,aucuns,aussi,autre,avant,avec,avoir,bon,car,ce,cela,ces,ceux,chaque,ci,comme,comment,dans,des,du,dedans,dehors,depuis,deux,devrait,doit,donc,dos,droite,début,elle,elles,en,encore,essai,est,et,eu,fait,faites,fois,font,force,haut,hors,ici,il,ils,je,juste,la,le,les,leur,là,ma,maintenant,mais,mes,mine,moins,mon,mot,même,ni,nommés,notre,nous,nouveaux,ou,où,par,parce,parole,pas,personnes,peut,peu,pièce,plupart,pour,pourquoi,quand,que,quel,quelle,quelles,quels,qui,sa,sans,ses,seulement,si,sien,son,sont,sous,soyez,sujet,sur,ta,tandis,tellement,tels,tes,ton,tous,tout,trop,très,tu,valeur,voie,voient,vont,votre,vous,vu,ça,étaient,état,étions,été,être';
    
    query.replace(words_to_exclude, ' ');
    if ( query.length &gt; 0 ) { 
      jQuery(".qa-faqs").highlight(query.split(" "), {className : 'showme'} );

      if ( jQuery('.showme').length == 0 ) {
        // This search has no matching results
        jQuery('.no-results-found').show();
      } 
      // Update reference
      jQuery(".qa-faq").attr('data-relevance', '0').hide().find("span.showme").each(function() {
        var incr = 1;
        if ( jQuery(this).parent().hasClass('qa-faq-anchor') ) {
          incr = incr + 2;
        }  
        var item = jQuery(this).removeClass('showme').parents('.qa-faq');
        item.attr('data-relevance', parseInt(item.attr('data-relevance')) + incr ).show();
      });

      // Sort questions
      var $wrapper = $('.qa-faqs');

      $wrapper.find('.qa-faq').sort(function (a, b) {
          return b.dataset.relevance - a.dataset.relevance;
      }).appendTo( $wrapper );	 

    }
    else {
      var $wrapper = $('.qa-faqs');

      $wrapper.find('.qa-faq').show().sort(function (a, b) {
          return b.dataset.origin - a.dataset.origin;
      }).appendTo( $wrapper );
    }

    $("html, body").animate({ scrollTop: $('.faq-container').offset().top }, 500, 'swing');
 
    return false;
  }


});
```
