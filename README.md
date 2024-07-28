import java.util.LinkedList;
import java.util.Queue;
import java.util.Scanner;

public class Main {
    public static void main(String[] args) {
        Scanner scanner = new Scanner(System.in);
        
        int N = scanner.nextInt();  // Number of processes
        
        Queue<Integer> callingOrder = new LinkedList<>();
        for (int i = 0; i < N; i++) {
            callingOrder.add(scanner.nextInt());
        }
        
        int[] idealOrder = new int[N];
        for (int i = 0; i < N; i++) {
            idealOrder[i] = scanner.nextInt();
        }
        
        int totalTime = 0;
        int idealIndex = 0;
        
        while (!callingOrder.isEmpty()) {
            if (callingOrder.peek() == idealOrder[idealIndex]) {
                callingOrder.poll();
                idealIndex++;
                totalTime++;
            } else {
                callingOrder.add(callingOrder.poll());
                totalTime++;
            }
        }
        
        System.out.println(totalTime);
        
        scanner.close();
    }
}
