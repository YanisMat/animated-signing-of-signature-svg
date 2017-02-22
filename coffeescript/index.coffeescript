window.signature =
  initialize: ->
    $('.signature svg').each ->
      paths = $('path, circle, rect', this)
      delay = 0
      for path in paths
        length = path.getTotalLength()
        previousStrokeLength = speed || 0
        speed = if length < 100 then 20 else Math.floor(length)
        delay += previousStrokeLength + 100
        $(path).css('transition', 'none')
               .attr('data-length', length)
               .attr('data-speed', speed)
               .attr('data-delay', delay)
               .attr('stroke-dashoffset', length)
               .attr('stroke-dasharray', length + ',' + length)

  animate: ->
    $('.signature svg').each ->
      paths = $('path, circle, rect', this)
      for path in paths
        length = $(path).attr('data-length')
        speed = $(path).attr('data-speed')
        delay = $(path).attr('data-delay')
        $(path).css('transition', 'stroke-dashoffset ' + speed + 'ms ' + delay + 'ms linear')
               .attr('stroke-dashoffset', '0')
        
$(document).ready ->
  window.signature.initialize()

  $('button').on 'click', ->
    window.signature.initialize()
    setTimeout( ->
      window.signature.animate()
    , 500)

$(window).load ->
  window.signature.animate()