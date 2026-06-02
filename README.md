# Amazon-Delivery-Operations-Dashboard

**PL BELOW**
Źródło danych:
Dataset został pobrany programistycznie z Kaggle przy użyciu Pythona (kagglehub, pandas), co zapewnia powtarzalność i automatyzację procesu pobierania danych.

KOD:

import kagglehub
import pandas as pd
import os

path = kagglehub.dataset_download("sujalsuthar/amazon-delivery-dataset")
files=os.listdir(path)
csvfile=[f for f in files if f.endswith(".csv")][0]
fullpath=os.path.join(path,csvfile)
dataset=pd.read_csv(fullpath)
dataset


**Przetwarzanie danych i modelowanie**
Czyszczenie i przygotowanie danych wykonane w Power Query (obsługa brakujących wartości i problemów jakości danych)
Transformacja z jednej tabeli faktów do struktury modelu gwiazdy (fact + dimensions)
Tworzenie tabel wymiarów (np. Traffic, Weather, Area, Category) z wykorzystaniem referencji w celu zapewnienia skalowalności i spójności modelu
Implementacja kluczy sztucznych (surrogate keys) w celu uniknięcia relacji wiele-do-wielu
Utworzenie dodatkowej kolumny grupującej kategorie w celu zmniejszenia kardynalności i poprawy czytelności wizualizacji
Połączenie przekształconej tabeli kategorii z tabelą faktów w modelu danych
Zrzut ekranu znajduje z resztą zdjęć dot. projektu

**KPI i metryki**
SLA (%) wyliczone na podstawie zdefiniowanych progów dla czasu procesowania i dostawy
(na potrzeby projektu przyjęto: maks. 10 minut dla przygotowania oraz 210 minut dla dostawy, ponieważ dataset nie zawierał zdefiniowanych założeń SLA)
Liczba zamówień oraz zamówienia na czas
Mediana czasu procesowania (bardziej odporna na wartości odstające niż średnia)
Czas end-to-end (Order → Pickup → Delivery)

**Wizualizacja i design**

Interfejs dashboardu zaprojektowany i przygotowany w Figma (warstwa frontendowa)
Nacisk na czytelną prezentację KPI, analizę trendów oraz wsparcie decyzji operacyjnych

**Analiza**

Identyfikacja wąskich gardeł poprzez analizę czasu procesowania
Analiza wpływu czynników zewnętrznych takich jak natężenie ruchu, pogoda oraz typ obszaru
Segmentacja według kategorii, regionu oraz warunków operacyjnych
Analiza zależności między wolumenem operacyjnym a efektywnością

**Stack technologiczny**

Python (pandas, kagglehub)
Power Query / Power BI (modelowanie danych, DAX)
Figma (projekt dashboardu / frontend)


**ENG BELOW**


**Data Source**:The dataset was programmatically retrieved from Kaggle using Python (kagglehub, pandas), ensuring reproducibility and automated data ingestion.
CODE:
import kagglehub
import pandas as pd
import os

path = kagglehub.dataset_download("sujalsuthar/amazon-delivery-dataset")
files=os.listdir(path)
csvfile=[f for f in files if f.endswith(".csv")][0]
fullpath=os.path.join(path,csvfile)
dataset=pd.read_csv(fullpath)
dataset


**Data Processing & Modeling**
Data cleaning and preprocessing performed in Power Query (handling missing values and data quality issues)
Transformation from a single fact table into a structured star schema model (fact + dimensions)
Creation of dimension tables (e.g., Traffic, Weather, Area, Category) using reference queries to ensure scalability and model consistency

**Implementation of surrogate keys where needed to avoid many-to-many relationships**
Created a derived category grouping to reduce cardinality and improve visualization clarity  
Linked the transformed category dimension to the fact table within the data model  
See attached screenshot for reference

**KPI & Metrics**
SLA (%) based on defined thresholds for processing and delivery time  
  (for the purpose of this project, SLA assumptions were defined as: max 10 minutes for preparation time and 210 minutes for delivery time, due to the lack of predefined SLA targets in the dataset)  
Total Orders and On-Time Orders  
Median Processing Time (preferred over average for robustness)  
End-to-End Processing Time (Order → Pickup → Delivery) 

**Visualization & Design**
Dashboard UI designed and prototyped in Figma (frontend layer)
Focus on clear KPI exposure, trend analysis, and operational decision support

**Analysis**
Bottleneck identification through processing time decomposition
Impact analysis of external factors such as traffic (road congestion), weather, and area type
Segmentation by category, region, and operational conditions
Correlation between operational load (volume) and performance metrics

**Tech Stack**
Python (pandas, kagglehub)
Power Query / Power BI (data modeling, DAX)
Figma (dashboard design / frontend)


