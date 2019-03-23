def BranchAndBoundMotifSearch(DNA,t,n,l):
    s_dla_drzewa = [1 for i in range(t)]
    s_dla_score = [ 0 for i in range(t)]
    bestScore = 0
    i = 0
    while (True):
        
        if (i < t):
            optimisticScore = score.best_score(s_dla_score, DNA, i)[0] + (t-i)*l  
#            print(s_dla_drzewa,optimisticScore)
            optimisticScore = optimisticScore + (t-i) *l
            
            if (optimisticScore < bestScore):
                s_dla_drzewa, i = funkcje_drzewo.Bypass(s_dla_drzewa,i,t,n-l+1)
                s_dla_score = [s_dla_drzewa[i]-1 for i in range(t)]
            else:
                s_dla_drzewa, i = funkcje_drzewo.NextVertex(s_dla_drzewa,i,t,n-l+1)
                s_dla_score = [s_dla_drzewa[i]-1 for i in range(t)]
        else:
            s_dla_score = [s_dla_drzewa[i]-1 for i in range(t)]
            score_1,motif = score.best_score(s_dla_score,DNA,l)
#            print(s_dla_score)
            if (score_1 > bestScore):
                bestScore = score_1
                the_best_motif = motif
                best_dna_lokalizacja = s_dla_score
            s_dla_drzewa, i = funkcje_drzewo.NextVertex(s_dla_drzewa,i,t,n-l+1)
        if (sum(s_dla_drzewa) == 0):
            break
    return bestScore, the_best_motif,best_dna_lokalizacja
