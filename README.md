{
  "nbformat": 4,
  "nbformat_minor": 0,
  "metadata": {
    "colab": {
      "provenance": [],
      "authorship_tag": "ABX9TyO2tQdHzd/sHytHFebdr98X",
      "include_colab_link": true
    },
    "kernelspec": {
      "name": "python3",
      "display_name": "Python 3"
    },
    "language_info": {
      "name": "python"
    }
  },
  "cells": [
    {
      "cell_type": "markdown",
      "metadata": {
        "id": "view-in-github",
        "colab_type": "text"
      },
      "source": [
        "<a href=\"https://colab.research.google.com/github/gaju45/python-EDA-on-Data-Science-salaries-2023/blob/main/README.md\" target=\"_parent\"><img src=\"https://colab.research.google.com/assets/colab-badge.svg\" alt=\"Open In Colab\"/></a>"
      ]
    },
    {
      "cell_type": "markdown",
      "source": [
        "#**Introduction**\n",
        "\n",
        "![download.jpg](data:image/jpeg;base64,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)\n",
        "\n",
        "This is an EDA project that explores the Data Science Salaries in 2023 dataset. The purpose of this project is to gain insights into the current trends and patterns of salaries in the data science industry. The dataset was obtained from Kaggle website and contains information on various features such as job title, years of experience, education level, location, and salary.\n",
        "\n",
        "# **Dataset**\n",
        "\n",
        "The dataset used in this project can be found on Kaggle website under the title \"Data Science Salaries in 2023\". It consists of a CSV file with over 10,000 rows and 11 columns. The columns include:\n",
        "\n",
        "Data Science Job Salaries Dataset contains 11 columns, each are:\n",
        "\n",
        "1.   work_year:\n",
        "2.   experience_level:\n",
        "3.   employment_levelz:\n",
        "4.   job_title:\n",
        "5.   salary:\n",
        "6.   salary_currency:\n",
        "7.   salaryinsd:\n",
        "8.   employee_residence:\n",
        "9.   remote_ratio:\n",
        "10.  company_location:\n",
        "11.  company_size:\n",
        "\n",
        "#**Methodology**\n",
        "\n",
        "The methodology used in this project involves performing exploratory data analysis on the dataset to gain insights into the patterns and trends of salaries in the data science industry. The analysis includes data cleaning, data visualization, and statistical analysis.\n",
        "\n",
        "# **Results**\n",
        "\n",
        "The results of the analysis are presented in the Jupyter Notebook file Data_Science_Salaries_EDA.ipynb. The findings include insights into the distribution of salaries based on job title, years of experience, education level, and location. The analysis also reveals the correlation between various features and their impact on the salary.\n",
        "\n",
        "#**Conclusion**\n",
        "In conclusion, this project provides valuable insights into the current trends and patterns of salaries in the data science industry. The findings can be used by individuals and companies to make informed decisions about salaries and job offers.\n",
        "\n"
      ],
      "metadata": {
        "id": "5NY9mKVXxbBX"
      }
    },
    {
      "cell_type": "code",
      "source": [],
      "metadata": {
        "id": "uRc2cRTuS1gY"
      },
      "execution_count": null,
      "outputs": []
    }
  ]
}