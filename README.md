# SHIVAM
import java.util.ArrayList;

abstract class Employee {
    private String name ;
    private int id ;
    public Employee (String name ,int id ){
        this.name =name;
        this.id=id;
    }
    public String getName(){
        return name;
    }
    public int getId(){
        return id;
    }
    public abstract double calculateSalary();
    //override
    public String toString (){
        return "Employee[name="+name+", id="+id+" , salary="+calculateSalary()+"]";
    }
}
// To create full time employee class
class FullTimeEmployee extends Employee{
    private double monthSalary;
    public FullTimeEmployee(String name ,int id ,double monthlySalary){
        super(name , id );
        this.monthlySalary = monthlySalary;
    }
//@override
        public double calculateSalary(){
            double monthlySalary;
            return monthlySalary;
        }
    }

class PartTimeEmployee extends Employee {
    private int hoursWorked;
    private double hourlyRate ;

    public PartTimeEmployee ( String name,int id , int hoursWorked , double hourlyRate ){
        super(name , id );
        this.hoursWorked=hoursWorked;
        this.hourlyRate=hourlyRate;
    }

    public double calculateSalary(){
        return hoursWorked*hourlyRate ;
    }
}
class PayrollSystem{
    private ArrayList<Employee > employeeList;
     
    public void payrollSystem(){
        employeeList=new ArrayList<>();
    }
    public void addEmployee ( Employee employee ){
        employeeList.add( employee);
    }
    public void removeEmployee( int id ){
        Employee employeeToRemove=null;
        for (Employee employee: employeeList){
            if (employee.getId()==id){
                Employee employeeToremove = employee;
                break ;
            }
        }
        if ( employeeToRemove !=null){
            employeeList.remove(employeeToRemove);
        }
    }
    public void displayEmployee(){
        for(Employee employee: employeeList){
            System.out.println(employee);
        }
    }
}
public class Main {
    public static void main(String[] args) {
        PayrollSystem payrollSystem = new PayrollSystem();

        FullTimeEmployee emp1 = new FullTimeEmployee("Vikas", 1, 75000);
        PartTimeEmployee emp2 = new PartTimeEmployee("Alexander", 2, 40, 300);

        payrollSystem.addEmployee(emp1);
        payrollSystem.addEmployee(emp2);

        System.out.println("Initial Employee Details:");
        payrollSystem.displayEmployee();

        System.out.println("Removing Employee with ID 2");
        payrollSystem.removeEmployee(2);

        System.out.println("Remaining Employee Details:");
        payrollSystem.displayEmployee();
    }
}




