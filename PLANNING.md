# Planning

## Main Features

- Browse cocktail recipes

- Search for cocktail recipes
  - name
  - ingredients

- Cocktail builder
  - save recipes to account

- Record home ingredients
  - save ingredients to account

- Cocktail suggestions based on home ingredients

### Pages

- Landing
  - Log in, sign up

- Dashboard
  - Dashboard
  - Search Recipes
    - Search by name
    - Search by ingredients
  - My Bar
    - Manage ingredients
    - Search/sort ingredients by name, category, liquor type
  - Builder
    - Add ingredients
    - Save recipes
  - My Recipes

## Data

```
model Cocktail {
  cocktail_id    Int         @id @default(autoincrement())
  name           String
  description    String
  glass_type     String
  instructions   String
  ingredients    CocktailIngredient[]
  garnishes      CocktailGarnish[]
}

model Ingredient {
  ingredient_id  Int         @id @default(autoincrement())
  name           String
  category       String
  liquor_type    String?
}

model Garnish {
  garnish_id     Int         @id @default(autoincrement())
  name           String
}

model CocktailIngredient {
  cocktail       Cocktail    @relation(fields: [cocktail_id], references: [cocktail_id])
  ingredient     Ingredient  @relation(fields: [ingredient_id], references: [ingredient_id])
  quantity       String
  @@id([cocktail_id, ingredient_id])
}

model CocktailGarnish {
  cocktail       Cocktail    @relation(fields: [cocktail_id], references: [cocktail_id])
  garnish        Garnish     @relation(fields: [garnish_id], references: [garnish_id])
  quantity       String
  @@id([cocktail_id, garnish_id])
}
```