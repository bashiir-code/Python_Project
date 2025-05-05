# Python_Project
python Movies dataset correlation project
\documentclass[12pt]{article}
\usepackage[a4paper, margin=1in]{geometry}
\usepackage{graphicx}
\usepackage{hyperref}
\usepackage{enumitem}
\usepackage{longtable}

\title{🎬 Movie Industry Correlation Analysis (1986--2016)}
\author{}
\date{}

\begin{document}

\maketitle

\section*{📁 Project Description}

This project presents an exploratory data analysis (EDA) on a dataset of 6,820 movies released between 1986 and 2016. The primary goal is to uncover \textbf{correlations and patterns} that help explain the factors contributing to a movie's commercial and critical success.

The dataset includes numerical and categorical features such as budget, gross revenue, IMDb ratings, user votes, genre, and key personnel (director, writer, and lead actor/actress).

\vspace{1em}
The analysis addresses questions such as:
\begin{itemize}[itemsep=0.5em]
    \item Does a higher budget correlate with higher revenue?
    \item Is there a relationship between IMDb scores and box office performance?
    \item Which features have the strongest correlations with movie success?
    \item Do production companies or countries significantly influence outcomes?
\end{itemize}

\vspace{1em}
The tools and libraries used include:
\begin{itemize}[itemsep=0.5em]
    \item \texttt{Pandas}, \texttt{NumPy} for data manipulation
    \item \texttt{Seaborn}, \texttt{Matplotlib} for visualization
    \item \texttt{Jupyter Notebook} for analysis and reporting
\end{itemize}

\section*{📂 Dataset Features}

\begin{longtable}{|p{3.5cm}|p{10cm}|}
\hline
\textbf{Column} & \textbf{Description} \\
\hline
\texttt{name} & Name of the movie \\
\texttt{budget} & Budget of the movie (0 if unknown) \\
\texttt{gross} & Gross revenue earned \\
\texttt{company} & Production company \\
\texttt{country} & Country of origin \\
\texttt{director} & Movie director \\
\texttt{writer} & Writer of the script \\
\texttt{star} & Lead actor or actress \\
\texttt{genre} & Main genre of the movie \\
\texttt{rating} & Content rating (e.g., R, PG) \\
\texttt{score} & IMDb user rating \\
\texttt{votes} & Number of user votes \\
\texttt{released} & Release date (YYYY-MM-DD) \\
\texttt{runtime} & Duration in minutes \\
\texttt{year} & Year of release \\
\hline
\end{longtable}

\section*{🔍 Objective}

By calculating correlation coefficients and visualizing relationships between variables, this project seeks to provide data-driven insights into what drives a movie's success and how different features interact.

\end{document}
