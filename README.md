# Opensource Competitive-Coding
Solutions to coding questions
#include<queue>
using namespace std;

void printbfs(int **edges,int v,int sv,bool *visited){
    
    
    queue<int>q;
    q.push(sv);
    visited[sv]=true;
    while(q.size()>0){
     int f=q.front();
        cout<<f<<" ";
        q.pop();        
    for(int i=0;i<v;i++){
        
       
        if(f==i){
            continue;
        }
        
        if(edges[f][i]==1&&!visited[i]){
            q.push(i);
            visited[i]=true;
        }
    }
        
    }
    
    
    
    
}

int main() {
    int v, e;
    cin >> v >> e;

    int **edges=new int*[v];
    for(int i=0;i<v;i++){
        edges[i]=new int[v];
        for(int j=0;j<v;j++){
            edges[i][j]=0;
        }
    }
    
    for(int i=0;i<e;i++){
        int f,s;
        cin>>f>>s;
        edges[f][s]=1;
        edges[s][f]=1;
    }
    
    bool *visited= new bool[v];
    for(int i=0;i<v;i++){
        visited[i]=false;
    }

    for(int i=0;i<v;i++){
    if(!visited[i]){
    printbfs(edges,v,i,visited);
    }
    }
  return 0;
}
