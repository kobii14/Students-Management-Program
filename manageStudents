#include <stdio.h>
#include <stdlib.h>
#include <string.h>
#define D_0 '0'
#define D_1 '1'
#define D_2 '2'
#define D_3 '3'
#define D_4 '4'
#define D_5 '5'
#define D_6 '6'
#define D_7 '7'
#define D_8 '8'
#define D_9 '9'
#define D_0 '0'
#define NUM_OF_SSCANF_ARGS 3
#define VALID_ASCII 10
#define ID_LENGTH 10
#define ID_ERROR "ERROR: Id must have 10 digits and can not start with 0\n"
#define NUM_ERR "ERROR: Students number must be a positive, numerical number\n"
#define GRADE_ERROR_1 "ERROR: grade must be a numerical number between 0-100\n"
#define AGE_ERROR_1 "ERROR: age must be a numerical number between 18-120\n"
#define INFO_MSG "best student info is: "
#define ARR_SIZE_60 60
#define ARR_SIZE_20 20
#define NUM_OF_STUDENTS "Enter number of students. Then enter\n"
#define STUDENT_INFO "Enter student info. Then enter\n"
#define COMMA ','
#define SPACE ' '
#define LOWEST_GRADE 0
#define HIGHEST_GRADE 100
#define LOWEST_AGE 18
#define HIGHEST_AGE 120
#define GRADE_ERROR_2 "ERROR: Grade has to be a number between 0-100\n"
#define AGE_ERR_2 "ERROR: Age should be an integer "\
"between 18 and 120 (includes).\n"
#define COMMAND_BEST "best"
#define COMMAND_BUBBLE "bubble"
#define COMMAND_QUICK "quick"
#define COMMAND_USAGE "USAGE: <best/bubble/quick>\n"

typedef struct Student
{
    long int id;
    int grade;
    int age;
} Student;
/**
 * this function checks if all of the string is digits
 * @param num gets a string of numbers
 * @return 1 if there are only numbers, 0 otherwise
 */
int all_numbers (char num[])
{
  unsigned int length = strlen(num);
  unsigned int i = 0;
  while (i < length - 1)
    {
      if (num[i] == D_0 || num[i] == D_1 || num[i] == D_2 || num[i] == D_3 ||
          num[i] == D_4 || num[i] == D_5 || num[i] == D_6 ||
          num[i] == D_7 || num[i] == D_8 || num[i] == D_9)
        {
          i++;
        }
      else
        {
          return 0;
        }
    }
  return 1;
}
int all_numbers_dig (char num[])
{
  unsigned int length = strlen(num);
  unsigned int i = 0;
  while (i < length)
    {
      if (num[i] == D_0 || num[i] == D_1 || num[i] == D_2 || num[i] == D_3 ||
          num[i] == D_4 || num[i] == D_5 || num[i] == D_6 ||
          num[i] == D_7 || num[i] == D_8 || num[i] == D_9)
        {
          i++;
        }
      else
        {
          return 0;
        }
    }
  return 1;
}
/**
 * checks if the input of students number is valid
 * @param std_num string of numbers
 * @return 1 if valid, 0 otherwise
 */
int student_num_check (char std_num[])
{
  if (all_numbers(std_num) == 0)
    {
      printf(NUM_ERR);
      return 0;
    }
  int int_num;
  int check_1 = sscanf(std_num, "%d",  &int_num);
  if (check_1 != 1)
    {
      return EXIT_FAILURE;
    }
  if (int_num == 0)
    {
      printf(NUM_ERR);
      return 0;
    }
  return 1;
}
/**
 * checks if the id is valid by the correct parameters
 * @param id string of id
 * @return 1 if valid, 0 otherwise
 */
int id_check (char id[])
{
  unsigned int length = (int) strlen(id);
  if (all_numbers_dig(id) == 0 || id[0] == D_0 || length != ID_LENGTH)
    {
      printf(ID_ERROR);
      return 0;
    }
  return 1;
}
/**
 * checks if the grade is valid by the correct parameters
 * @param grade string of grade
 * @return 1 if valid, 0 otherwise
 */
int grade_check (char grade[])
{
  if (all_numbers_dig(grade) == 0)
    {
      printf(GRADE_ERROR_1);
      return 0;
    }
  return 1;
}
/**
 * checks if the age is valid by the correct parameters
 * @param age string of id
 * @return 1 if valid, 0 otherwise
 */
int age_check(char age[])
{
  if (all_numbers_dig(age) == 0)
    {
      printf(AGE_ERROR_1);
      return 0;
    }
  return 1;
}
/**
 * gets a pointer to the start and the end of an array and checks the best
 * student's rate
 * @param start pointer to the start if the array
 * @param end pointer to the end of the array
 */
void best_student(Student *start, Student *end)
{
  float best_rate = 0;
  float rate = 0;
  Student *best_pointer = start;
  double grade;
  double age;
  while (start != end)
    {
      grade = start->grade;
      age = start->age;
      rate = grade / age;
      if (rate > best_rate)
        {
          best_rate = rate;
          best_pointer = start;
        }
      start++;
    }
  printf("%s%ld,%d,%d\n", INFO_MSG, best_pointer->id,
         best_pointer->grade, best_pointer->age);
}
/**
 * helper function to the recursive quick sort
 * @param start pointer to the start if the array
 * @param end pointer to the end of the array
 * @return a pointer to the specific cell in the array
 */
Student *partition(Student *start, Student *end)
{
  Student *new_end = end - 1;
  long int id_keeper = 0;
  int grade_keeper = 0;
  int age_keeper = 0;
  int pivot = new_end->age;
  Student *i = (start - 1);
  for (Student *j = start; j <= new_end - 1; j++)
    {
      if (j->age <= pivot)
        {
          i++;
          id_keeper = i->id;
          grade_keeper = i->grade;
          age_keeper = i->age;
          i->id = j->id;
          i->grade = j->grade;
          i->age = j->age;
          j->id = id_keeper;
          j->grade = grade_keeper;
          j->age = age_keeper;
        }
    }
  id_keeper = (i+1)->id;
  grade_keeper = (i+1)->grade;
  age_keeper = (i+1)->age;
  (i+1)->id = new_end->id;
  (i+1)->grade = new_end->grade;
  (i+1)->age = new_end->age;
  new_end->id = id_keeper;
  new_end->grade = grade_keeper;
  new_end->age = age_keeper;
  return (i+1);
}
/**
 * a function that sorts an array by quick sort
 * @param start pointer to the start if the array
 * @param end pointer to the end of the array
 */
void quick_sort(Student *start, Student *end)
{
  if (start < end)
    {
      Student *pi = partition(start, end);
      quick_sort(start, pi);
      quick_sort(pi + 1, end);
    }
}
/**
 * a function that sorts an array by bubble sort
 * @param start pointer to the start if the array
 * @param end pointer to the end of the array
 */
void bubble_sort(Student *start, Student *end)
{
  Student *copy_str = start;
  Student *helper_pointer_1 = NULL;
  Student *helper_pointer_2 = NULL;
  long int id_keeper = 0;
  int grade_keeper = 0;
  int age_keeper = 0;
  int counter = -1;
  while (start + counter < end)
    {
      counter++;
      helper_pointer_2 = start + 1;
      helper_pointer_1 = start;
      while (helper_pointer_2 < end - counter)
        {
          if (helper_pointer_1->grade > helper_pointer_2->grade)
            {
              id_keeper = helper_pointer_1->id;
              grade_keeper = helper_pointer_1->grade;
              age_keeper = helper_pointer_1->age;
              helper_pointer_1->id = helper_pointer_2->id;
              helper_pointer_1->grade = helper_pointer_2->grade;
              helper_pointer_1->age = helper_pointer_2->age;
              helper_pointer_2->id = id_keeper;
              helper_pointer_2->grade = grade_keeper;
              helper_pointer_2->age = age_keeper;
            }
          helper_pointer_2++;
          helper_pointer_1++;
        }
    }
  while (copy_str != end)
    {
      printf("%ld,%d,%d\n", copy_str->id, copy_str->grade, copy_str->age);
      copy_str++;
    }
}
/**
 * a function that prints the sorted array
 * @param start pointer to the start if the array
 * @param end pointer to the end of the array
 */
void print_quick_sort(Student *start, Student *end)
{
  while (start <= end)
    {
      printf("%ld,%d,%d\n", start->id, start->grade, start->age);
      start++;
    }
}

int main (int argc, char *argv[])
{
  //checks the valid of argc value
  if (argc != 2)
    {
      printf(COMMAND_USAGE);
      return EXIT_FAILURE;
    }
  int is_best = strcmp(argv[1], COMMAND_BEST);
  int is_bubble = strcmp(argv[1], COMMAND_BUBBLE);
  int is_quick = strcmp(argv[1], COMMAND_QUICK);
  if (argc != 2 || (is_best && is_bubble && is_quick))
    {
      printf(COMMAND_USAGE);
      return EXIT_FAILURE;
    }
  int student_num = 0;
  char student_num_str[ARR_SIZE_60];
  char student_info_str_2[ARR_SIZE_60];
  //asks from the user the number of students and checks if the number is valid
  do
    {
      printf(NUM_OF_STUDENTS);
      char *get_check_2 = fgets(student_num_str, ARR_SIZE_60 , stdin);
      if (get_check_2 == NULL)
        {
          return EXIT_FAILURE;
        }
    }
  while (student_num_check(student_num_str) == 0
  || *student_num_str == VALID_ASCII);
  int check_1 = sscanf(student_num_str, "%d", &student_num);
  if (check_1 != 1)
    {
      return EXIT_FAILURE;
    }
    //allocating a dynamic memory for the user's input
  Student *students_arr = malloc (sizeof(Student) * student_num);
  if (students_arr == NULL)
    {
      return EXIT_FAILURE;
    }
  char id_num[ARR_SIZE_20];
  char grade[ARR_SIZE_20];
  char age[ARR_SIZE_20];
  long int id_num_int;
  int grade_int;
  int age_int;
  int students_counter = 0;
  int flag = 1;
  //asks the user to input students info and checks if input is valid
  do
    {
      flag = 1;
      while (student_num != students_counter)
        {
          printf(STUDENT_INFO);
          char *get_check_1 = fgets(student_info_str_2, ARR_SIZE_60 , stdin);
          if (get_check_1 == NULL)
            {
              free(students_arr);
              return EXIT_FAILURE;
            }
          char *p = student_info_str_2;
          int comma_counter = 0;
          int id_length = 0;
          int grade_length = 0;
          int age_length = 0;
          unsigned int length = strlen(student_info_str_2);
          for (unsigned int i = 0; i < length; i++)
            {
              if (comma_counter == 0)
                {
                  id_length++;
                }
              else if (comma_counter == 1)
                {
                  grade_length++;
                }
              else if (comma_counter == 2)
                {
                  age_length++;
                }
              if (*p == COMMA)
                {
                  *p = SPACE;
                  comma_counter++;
                }
              p++;
            }
          if (id_length - 1 != ID_LENGTH)
            {
              printf (ID_ERROR);
              flag = 0;
              break;
            }
          if (grade_length - 1 == 0)
            {
              printf(GRADE_ERROR_1);
              flag = 0;
              break;
            }
          if (age_length - 1 == 0)
            {
              printf(AGE_ERROR_1);
              flag = 0;
              break;
            }
          int check_2 = sscanf(student_info_str_2, "%s %s %s",
                               id_num, grade, age);
          if (check_2 != NUM_OF_SSCANF_ARGS)
            {
              free(students_arr);
              return EXIT_FAILURE;
            }
          if (!id_check(id_num) || !grade_check(grade) || !age_check(age))
            {
              flag = 0;
              break;
            }
          int check_3 = sscanf(student_info_str_2, "%ld %d %d",
                               &id_num_int, &grade_int, &age_int);
          if (check_3 != NUM_OF_SSCANF_ARGS)
            {
              free(students_arr);
              return EXIT_FAILURE;
            }
          if (grade_int < LOWEST_GRADE || grade_int > HIGHEST_GRADE)
            {
              printf(GRADE_ERROR_2);
              flag = 0;
              break;
            }
          if (age_int < LOWEST_AGE || age_int > HIGHEST_AGE)
            {
              printf(AGE_ERR_2);
              flag = 0;
              break;
            }
          int check_4 = sscanf (student_info_str_2, "%ld %d %d",
                                &students_arr[students_counter].id,
                                &students_arr[students_counter].grade,
                                &students_arr[students_counter].age);
          if (check_4 != NUM_OF_SSCANF_ARGS)
            {
              free (students_arr);
              return EXIT_FAILURE;
            }
          students_counter++;
        }
    }
  while (flag == 0);
  //checks what is the program the user wants to run
  if (is_best == 0)
    {
      best_student(students_arr, students_arr + student_num);
    }
  else if (is_bubble == 0)
    {
      bubble_sort(students_arr, students_arr + student_num);
    }
  else if (is_quick == 0)
    {
      quick_sort(students_arr, students_arr + student_num);
      print_quick_sort(students_arr, students_arr + student_num - 1);
    }
  free(students_arr);
  return EXIT_SUCCESS;
}
