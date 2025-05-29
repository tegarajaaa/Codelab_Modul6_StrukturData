# Codelab_Modul6_StrukturData
import java.util.*;

public class LogistikGraph {
    private Map<String, List<String>> adjList = new HashMap<>();
    private List<String> vertices = Arrays.asList("A", "B", "C", "D", "E");

    public LogistikGraph() {
        for (String v : vertices) {
            adjList.put(v, new ArrayList<>());
        }
        addEdge("A", "B");
        addEdge("A", "C");
        addEdge("B", "D");
        addEdge("C", "D");
        addEdge("C", "E");
        addEdge("D", "E");
        addEdge("E", "A");
    }

    private void addEdge(String from, String to) {
        adjList.get(from).add(to);
    }

    public void printAdjacencyMatrix() {
        System.out.println("Adjacency Matrix:");
        System.out.print("    ");
        for (String v : vertices) System.out.print(v + " ");
        System.out.println();
        for (String from : vertices) {
            System.out.print(from + " : ");
            for (String to : vertices) {
                System.out.print(adjList.get(from).contains(to) ? "1 " : "0 ");
            }
            System.out.println();
        }
    }

    public void bfs(String start) {
        System.out.print("BFS dari " + start + ": ");
        Set<String> visited = new HashSet<>();
        Queue<String> queue = new LinkedList<>();
        visited.add(start);
        queue.add(start);
        while (!queue.isEmpty()) {
            String curr = queue.poll();
            System.out.print(curr + " ");
            for (String neighbor : adjList.get(curr)) {
                if (!visited.contains(neighbor)) {
                    visited.add(neighbor);
                    queue.add(neighbor);
                }
            }
        }
        System.out.println();
    }

    public void dfs(String start) {
        System.out.print("DFS dari " + start + ": ");
        Set<String> visited = new HashSet<>();
        dfsRecursive(start, visited);
        System.out.println();
    }

    private void dfsRecursive(String curr, Set<String> visited) {
        visited.add(curr);
        System.out.print(curr + " ");
        for (String neighbor : adjList.get(curr)) {
            if (!visited.contains(neighbor)) {
                dfsRecursive(neighbor, visited);
            }
        }
    }

    public static void main(String[] args) {
        LogistikGraph graph = new LogistikGraph();
        graph.printAdjacencyMatrix();
        graph.bfs("A");
        graph.dfs("A");
    }
}
