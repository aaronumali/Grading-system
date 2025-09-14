/*
 * Click nbfs://nbhost/SystemFileSystem/Templates/Licenses/license-default.txt to change this license
 * Click nbfs://nbhost/SystemFileSystem/Templates/Classes/Class.java to edit this template
 */

/**
 *
 * @author aaron
 */

import java.util.Scanner;

public class StudentGrading {

    public static void main(String[] args) {
        Scanner sc = new Scanner(System.in);

        // Input number of students and subjects
        System.out.print("Enter the number of students: ");
        int numberOfStudents = sc.nextInt();
        System.out.print("Enter the number of subjects: ");
        int numberOfSubjects = sc.nextInt();

        // Declare arrays
        String[] subjects = new String[numberOfSubjects];
        double[][][] grades = new double[numberOfStudents][numberOfSubjects][4];
        double[][] finalGrades = new double[numberOfStudents][numberOfSubjects];

        // Input subject names
        System.out.println("Enter the subject names:");
        for (int i = 0; i < numberOfSubjects; i++) {
            System.out.print("Subject " + (i + 1) + ": ");
            subjects[i] = sc.next();
        }

        // Input grades
        for (int student = 0; student < numberOfStudents; student++) {
            System.out.println("\nEntering grades for Student " + (student + 1) + ":");
            for (int subject = 0; subject < numberOfSubjects; subject++) {
                System.out.println("Subject: " + subjects[subject]);
                for (int quarter = 0; quarter < 4; quarter++) {
                    System.out.print("Quarter " + (quarter + 1) + ": ");
                    grades[student][subject][quarter] = sc.nextDouble();
                }
                // Calculate final grade for the subject
                double total = 0;
                for (int quarter = 0; quarter < 4; quarter++) {
                    total += grades[student][subject][quarter];
                }
                finalGrades[student][subject] = total / 4;
            }
        }

        // Display grades in a table format
        for (int student = 0; student < numberOfStudents; student++) {
            System.out.println("\nGrades for Student " + (student + 1) + ":");
            System.out.printf("%-10s %-10s %-10s %-10s %-10s %-10s%n", "Subject", "Q1", "Q2", "Q3", "Q4", "Final Grade");
            for (int subject = 0; subject < numberOfSubjects; subject++) {
                System.out.printf("%-10s ", subjects[subject]);
                for (int quarter = 0; quarter < 4; quarter++) {
                    System.out.printf("%-10.2f ", grades[student][subject][quarter]);
                }
                System.out.printf("%-10.2f%n", finalGrades[student][subject]);
            }

            // Calculate and display the general average
            double generalAverage = 0;
            for (int subject = 0; subject < numberOfSubjects; subject++) {
                generalAverage += finalGrades[student][subject];
            }
            generalAverage /= numberOfSubjects;
            System.out.printf("General Average: %.2f%n", generalAverage);
        }

        sc.close();
    }
}
