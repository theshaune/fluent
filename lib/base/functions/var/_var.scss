/* ==========================================================================
  
  var()

  Description;
    var() is an extension of map_get()
    This allows you to get deep variables.
 
  Example use;
    $map: (
      brand: (
        primary: #000000
      )
    );

    div {
      color: var($map, brand primary);
    }

   ========================================================================== */

@function var($map, $keys: null) {
  @if ($keys != null){
    @each $key in $keys {
      $map: map-get($map, $key);
    }
  }
  @return $map;
}
