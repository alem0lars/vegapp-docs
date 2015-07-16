# Analysis

## Problem Interaction

### Navigation

*The navigation defines the main user interactions: those which
triggers navigation inside the application, i.e. how the
end-user should use it in order to change environments and to access its
features.*

The following diagram defines the main navigation flow, by defining:

- **The Screens** (*ellipses*): these are the main views the
  user interacts with:
  Here we don't consider small views or details.
  Even *how* those screens are implemented will be specific to
  the particular device and technology chosen.

- **The Main Actions** that can be taken (*arrows*): An arrows triggers
  a transition from a view to another (possibly the same) view. 
  Here we don't consider small actions or interactions but only the
  macro interactions: those which usually trigger screen changes.

```dot
digraph G {
  node [shape = ellipse, style = filled];

  // {{{ Screens.

  StartScreen [label = "Start Screen", color = violetred4, fillcolor = violetred2];

  subgraph clusterprofile {
    label = "Profile";
    style = bold;
    color = plum2;
    fontcolor = plum2;
    fontsize = 16;
    node [color = plum4, fillcolor = plum2];

    ProfileShow [label = "Profile (show)"];
    ProfileNew [label = "Profile (new)"];
    ProfileEdit [label = "Profile (edit)"];
  }

  subgraph clusterdish {
    label = "Dish";
    style = bold;
    color = springgreen2;
    fontcolor = springgreen2;
    fontsize = 16;
    node [color = springgreen4, fillcolor = springgreen2];

    Dishes [label = "Dishes list"];
    DishShow [label = "Dish (show)"];
    DishNew [label = "Dish (new)"];
    DishEdit [label = "Dish (edit)"];
  }

  subgraph clusteringredient {
    label = "Ingredient";
    style = bold;
    color = steelblue2;
    fontcolor = steelblue2;
    fontsize = 16;
    node [color = steelblue4, fillcolor = steelblue2];

    Ingrs [label = "Ingredients list"];
    IngrShow [label = "Ingredient (show)"];
    IngrNew [label = "Ingredient (new)"];
    IngrEdit [label = "Ingredient (edit)"];
  }

  subgraph clusterattribute {
    label = "Attribute";
    style = bold;
    color = yellow2;
    fontcolor = yellow2;
    fontsize = 16;
    node [color = yellow4, fillcolor = yellow2];

    Attrs [label = "Attributes list"];
    AttrShow [label = "Attribute (show)"];
    AttrNew [label = "Attribute (new)"];
    AttrEdit [label = "Attribute (edit)"];
  }

  // }}}

  // {{{ Actions.

  // {{{ Start Screen.

  StartScreen -> ProfileShow [label = "login"];
  StartScreen -> ProfileNew [label = "register"];

  // }}}

  // {{{ Profile.

  ProfileShow -> StartScreen [label = "logout"];
  ProfileShow -> ProfileEdit [label = "edit"];
  ProfileShow -> Dishes [label = "list"];
  ProfileShow -> Dishes [label = "search"];
  ProfileShow -> DishNew [label = "new"];

  ProfileNew -> ProfileShow [label = "submit"];

  ProfileEdit -> ProfileShow [label = "update"];

  // }}}

  // {{{ Dishes.

  Dishes -> Dishes [label = "search"];
  Dishes -> DishNew [label = "new"];
  Dishes -> DishShow [label = "show"];
  Dishes -> DishEdit [label = "edit"];

  DishShow -> DishShow [label = "star"];
  DishShow -> DishEdit [label = "edit"];
  DishShow -> Dishes [label = "delete"];
  DishShow -> IngrShow [label = "show ingr"];
  DishShow -> AttrShow [label = "show attr"];

  DishNew -> DishShow [label = "create"];
  DishNew -> IngrShow [label = "show ingr"];
  DishNew -> Ingrs [label = "add ingr"];
  DishNew -> DishNew [label = "remove ingr"];
  DishNew -> IngrEdit [label = "copy & edit ingr"];
  DishNew -> AttrShow [label = "show attr"];
  DishNew -> Attrs [label = "add attr"];
  DishNew -> DishNew [label = "remove attr"];
  DishNew -> AttrEdit [label = "copy & edit attr"];

  DishEdit -> DishShow [label = "update"];
  DishEdit -> Dishes [label = "delete"];
  DishEdit -> IngrShow [label = "show ingr"];
  DishEdit -> Ingrs [label = "add ingr"];
  DishEdit -> DishEdit [label = "remove ingr"];
  DishEdit -> IngrEdit [label = "copy & edit ingr"];
  DishEdit -> AttrShow [label = "show attr"];
  DishEdit -> Attrs [label = "add attr"];
  DishEdit -> DishEdit [label = "remove attr"];
  DishEdit -> AttrEdit [label = "copy & edit attr"];

  // }}}

  // {{{ Ingrs.

  Ingrs -> Ingrs [label = "search"];
  Ingrs -> IngrNew [label = "new"];
  Ingrs -> IngrShow [label = "show"];
  Ingrs -> IngrEdit [label = "edit"];

  IngrShow -> IngrEdit [label = "edit"];
  IngrShow -> Ingrs [label = "delete"];
  IngrShow -> AttrShow [label = "show attr"];

  IngrNew -> IngrShow [label = "create"];
  IngrNew -> AttrShow [label = "show attr"];
  IngrNew -> Attrs [label = "add attr"];
  IngrNew -> IngrNew [label = "remove attr"];
  IngrNew -> AttrEdit [label = "copy & edit attr"];

  IngrEdit -> IngrShow [label = "update"];
  IngrEdit -> Ingrs [label = "delete"];
  IngrEdit -> AttrShow [label = "show attr"];
  IngrEdit -> Attrs [label = "add attr"];
  IngrEdit -> IngrEdit [label = "remove attr"];
  IngrEdit -> AttrEdit [label = "copy & edit attr"];

  // }}}

  // {{{ Attrs.

  Attrs -> Attrs [label = "search"];
  Attrs -> AttrNew [label = "new"];
  Attrs -> AttrShow [label = "show"];
  Attrs -> AttrEdit [label = "edit"];

  AttrShow -> AttrEdit [label = "edit"];
  AttrShow -> Attrs [label = "delete"];

  AttrNew -> AttrShow [label = "create"];

  AttrEdit -> AttrShow [label = "update"];
  AttrEdit -> Attrs [label = "delete"];

  // }}}

  // }}}

}
```

### Other interactions

Of course there are a lot of interactions not described in the section
*Navigation*. Even the described ones can have a lot of details attached.
