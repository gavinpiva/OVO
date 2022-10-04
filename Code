#Gavin Piva OVO
import numpy as np
import matplotlib.pyplot as plt
import argparse

class OVO:
    def __init__(self):
        data = np.loadtxt("data.dat")
        X, Y = data[:,:2], np.array(data[:,2], dtype='int')
        self.N = len(data)
        self.X = np.concatenate((np.ones((self.N,1)), X), axis=1)
        self.Y = Y
        self.data = data
        self.minus = np.zeros(2)
        self.plus = np.zeros(2)

    def PLA(self, X, Y):
        flag = False  # flag condition for seeing if the while loop needs to keep running
        W = np.zeros(3)
        while flag == False:  # while loop for all points
            flag = True
            for i in range(X.shape[0]):  # the size of the array
                prod = np.sign(np.dot(X[i, :], W))# sign of the dot product of the w and the coordinate array
                # print(self.Y[i])
                if prod != np.sign(Y[i]):  # condition to see if the point is in the correct spot
                    W = W + np.dot(X[i], Y[i])  # for correcting mistake
                    flag = False  # if all points are correct stop the while loop
        # W.reshape(2,W.shape[0])
        return W

    def train(self):
        # Train a model using One-Versus-One method.
        # Call PLA on every pair of groups. 
        # The purpose of this function is to calculate W ang Groups.

        self.W = np.zeros((6, 3)) # Each row of W is one boundary line between two groups. 
        self.Groups = np.zeros((6,2), dtype=int) # Each row of Groups is the types of two groups, where the first number is the type of the positive side and the second number is the type of the negative side. Type is an integer from 0 to 3.

        k = 0
        for i in range(3):
            for j in range(i+1, 4):
                self.Groups[k] = [i, j]
                k += 1
        print(self.Groups)
        k = 0
        for i, j in (self.Groups):
            irowX = self.X[self.Y == i]
            jrowX = self.X[self.Y == j]
            irowY = np.ones(len(self.X[self.Y == i]))
            jrowY = np.ones(len(self.X[self.Y == j]))
            jrowYneg = np.negative(jrowY)
            Xstack = np.vstack((irowX, jrowX))
            Ystack = np.concatenate((irowY, jrowYneg))
            self.W[k] = self.PLA(Xstack, Ystack)
            k+=1


    def find_group(self, point):

        maj = [0]*6
        point = [1,point[0],point[1]]
        for i in range(len(maj)):
            decision = np.sign(np.dot(point, self.W[i]))
            # print(decision[i])
            if decision > 0:
                maj[i] = self.Groups[i,0]
            else:
                maj[i] = self.Groups[i,1]

        return max(set(maj), key=maj.count)

    def plot(self, type):
        M = 100
        grid = np.zeros((M**2, 3))
        p = np.linspace(-1,1,M)
        k=0
        for i in range(M):
            for j in range(M):
                grid[k] = [p[i], p[j], self.find_group([p[i],p[j]])]
                k+=1
        # plt.figure(figsize=(8, 8), dpi=80)
        style = ['rs', 'bs', 'ks', 'ys']
        for i in range(4): 
            data = grid[grid[:,2]==i]
            plt.plot(data[:,0], data[:,1], style[i])
        plt.xticks([], [])
        plt.yticks([], [])
        plt.xlim(-1,1)
        plt.ylim(-1,1)
        
        if type == "show":
            plt.show()
        elif type == "save":
            plt.savefig("result.png")
        else:
            print("type must be either show or save")

if __name__ == "__main__":
    obj = OVO()
    # Run 
    obj.train()
    # Show results
    obj.plot("show")
    # Save results
    # obj.plot("save")

