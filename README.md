# project31
# Beneddine Amel Biochimie appliquée 07/12/2025
# membres de groupe:(

                     # Beneddine Amel
                     # Benali Samia
                     # Meghelli Hichem
                     # Meghelli Souheil
                     # Bendada Ilyas Abderrezzak)

import pandas as pd

#Donnees : Séquences ADN, Longueur, Pourcentage de GC

data = {
   
    "séquence": ["ATGCGTACGTA","GCTAGCTAGGCC","ATGCGCGTAAGT","TACGATCGTA","ATGAAAGGCTT","CGTACGTAGC","TTAACCGGAT"],
    "Longueur": [11, 12, 12, 10, 11, 10, 10],
    "Pourcentage GC": [50, 66.67, 58.33, 40, 45.45, 60, 50],
}

# 1) Creation d'un DataFrame (tableau pandas)
df = pd.DataFrame(data)
print("**************** Creation et affichage *****************")

# Affichage du tableau
print("Tableau des séquences ADN :")
print(df, "\n\n")

# Opérations sur les tableaux:
print("************** longueur ***************")
# 2) Sélectionner la colonne "Longueur"
Longueur = df["Longueur"]
print(Longueur, "\n\n")

# 3)Filtrer les séquences dant la longueur est supérieur à 10
print("*************Filtrage  Longueur supérieur à  10 *************")
# Filtrer les séquences dant la longueur est supérieur a 10
filtered_df = df[df["Longueur"] > 10]
print(filtered_df, "\n\n")

# 4)Calculer la moyenne du pourcentage de GC avec 3 chiffres aprC(s la virgule
print("************* Calcul de la moyenne *************")
# Calculer la moyenne du pourcentage de GC avec 3 chiffres aprC(s la virgule
average_gc = df["Pourcentage GC"].mean()
print(f"Pourcentage moyen de GC : {average_gc:.3f}%", "\n\n")

# 5)Ajouter une nouvelle colonne
print("\n************* Ajout d'une nouvelle colonne catégorie GC *************\n")
# Ajouter une nouvelle colonne " CatC)gorie_gc "
df["catégorie GC"] = df["Pourcentage GC"].apply(lambda x: "Riche" if x > 55 else ("Moyen" if x >= 45 else "Faible"))

print(df, "\n\n")

# 6)Ajouter une colonne comptant les 'G' dans chaque séquence

df["Nb_G"] = df["séquence"].apply(lambda seq: seq.count("G"))

print("\n************Nombre de G dans chaque séquence **************\n")
print(df)

# 7) Calculer l'C)cart-type du %GC et de la longueur des sC)quences
print("\n************* C	carts-types ***********\n")
ecart_type_gc = df["Pourcentage GC"].std()
ecart_type_longueur = df["Longueur"].std()
print(f"C	cart-type du %GC : {ecart_type_gc:.2f}\n")
print(f"C	cart-type de la longueur : {ecart_type_longueur:.2f}\n")

# 8)sauvegarder le tbleau final en fichier CSV
df.to_csv("tableau_final_sequences.csv", index=False)
print("csv_loaded")







