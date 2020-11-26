enum nodes { A, B, C, D, E };

#include <stdio.h>
#include <limits.h>

#define NUM_OF_EDGES 14
#define NUM_OF_NODES 5

int visited[NUM_OF_NODES];

typedef struct {
	char src;
	char dest;
	int weight;
	int size;
}Edge;

typedef struct {
	char start;
	int shortestPath;
	char previous;
}Table;

Edge* edges[NUM_OF_EDGES];
Table* tables[NUM_OF_NODES];

void addEdge(Edge* edge, char src, char dest, int weight) {
	edge->src = src;
	edge->dest = dest;
	edge->weight = weight;
}

unsigned allVisited() {
	int cnt = 0;
	for (int i = 0; i < NUM_OF_NODES; i++) {
		if (visited[i] == 1)
			cnt++;
	}
	if (cnt == NUM_OF_NODES) return 1;

	return 0;
}

void init() {
	for (int i = 0; i < NUM_OF_EDGES; i++) {
		edges[i] = malloc(sizeof(Edge));
		edges[i]->size = 0;
	}

	for (int i = 0; i < NUM_OF_NODES; i++) {
		tables[i] = malloc(sizeof(Table));
		tables[i]->start = 'A' + i;
		tables[i]->shortestPath = INT_MAX;
		tables[i]->previous = NULL;
		visited[i] = 0;
	}
}

int main() {

	init();

	addEdge(edges[0], 'A', 'B', 7);
	addEdge(edges[1], 'A', 'C', 2);

	addEdge(edges[2], 'B', 'A', 7);
	addEdge(edges[3], 'B', 'C', 1);
	addEdge(edges[4], 'B', 'D', 3);

	addEdge(edges[5], 'C', 'A', 2);
	addEdge(edges[6], 'C', 'B', 1);
	addEdge(edges[7], 'C', 'D', 9);
	addEdge(edges[8], 'C', 'E', 5);

	addEdge(edges[9], 'D', 'B', 3);
	addEdge(edges[10], 'D', 'C', 9);
	addEdge(edges[11], 'D', 'E', 1);

	addEdge(edges[12], 'E', 'C', 5);
	addEdge(edges[13], 'E', 'D', 1);

	int startIndex = A;
	tables[A]->shortestPath = 0;
	visited[A] = 1;
	int cnt = 0;

	printf("Below table shows the shortest path constructed by Dijkstra's algorithm:\n");

	for (; ; ) {
		int shortestPath;
		visited[startIndex] = 1;
		if (allVisited()) break;
		

	

		/*i dont know this part*/
	}

	printf("\n");
	printf("startVertex shortestPath previousVertex\n");
	for (int i = 0; i < NUM_OF_NODES; i++) {
		printf("%c %d %c\n", tables[i]->start, tables[i]->shortestPath, tables[i]->previous);
	}
}
