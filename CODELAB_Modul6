import java.util.*;

class LogistikGraph {
    static final int SIZE = 5;
    static String[] nodes = {"A", "B", "C", "D", "E"};
    static int[][] adjMatrix = new int[SIZE][SIZE];

    // Mapping nama gudang ke indeks
    static int getIndex(String node) {
        for (int i = 0; i < SIZE; i++) {
            if (nodes[i].equals(node)) return i;
        }
        return -1;
    }

    // Tambahkan edge (arah: dari → ke)
    static void addEdge(String from, String to) {
        int i = getIndex(from);
        int j = getIndex(to);
        if (i != -1 && j != -1) {
            adjMatrix[i][j] = 1;
        }
    }

    // BFS
    static void bfs(String startNode) {
        boolean[] visited = new boolean[SIZE];
        Queue<Integer> queue = new LinkedList<>();

        int start = getIndex(startNode);
        visited[start] = true;
        queue.add(start);

        System.out.print("BFS dari " + startNode + ": ");
        while (!queue.isEmpty()) {
            int current = queue.poll();
            System.out.print(nodes[current] + " ");

            for (int i = 0; i < SIZE; i++) {
                if (adjMatrix[current][i] == 1 && !visited[i]) {
                    queue.add(i);
                    visited[i] = true;
                }
            }
        }
        System.out.println();
    }

    // DFS
    static void dfs(String startNode) {
        boolean[] visited = new boolean[SIZE];
        System.out.print("DFS dari " + startNode + ": ");
        dfsRecursive(getIndex(startNode), visited);
        System.out.println();
    }

    static void dfsRecursive(int current, boolean[] visited) {
        visited[current] = true;
        System.out.print(nodes[current] + " ");
        for (int i = 0; i < SIZE; i++) {
            if (adjMatrix[current][i] == 1 && !visited[i]) {
                dfsRecursive(i, visited);
            }
        }
    }

    // Cetak adjacency matrix
    static void printAdjacencyMatrix() {
        System.out.println("Adjacency Matrix:");
        for (int i = 0; i < SIZE; i++) {
            System.out.print(nodes[i] + ": ");
            for (int j = 0; j < SIZE; j++) {
                System.out.print(adjMatrix[i][j] + " ");
            }
            System.out.println();
        }
    }

    public static void main(String[] args) {
        // Tambahkan 7 jalur
        addEdge("A", "B");
        addEdge("A", "C");
        addEdge("B", "D");
        addEdge("C", "D");
        addEdge("D", "E");
        addEdge("E", "A");
        addEdge("B", "E");

        // Tampilkan adjacency matrix
        printAdjacencyMatrix();

        // Jalankan BFS dan DFS dari A
        bfs("A");
        dfs("A");
    }
}
