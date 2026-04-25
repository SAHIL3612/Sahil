import sys

def read_cases(data, idx, n, results):
    if n == 0:
        print('\n'.join(results))
        return

    x = int(data[idx])
    values = list(map(int, data[idx+1: idx+1+x]))

    if len(values) != x:
        results.append("1")
        read_cases(data, idx+1+x, n-1, results)
        return

    total = sum(
        map(lambda yn: yn**4,
            filter(lambda yn: yn <= 0, values))
    )

    results.append(str(total))
    read_cases(data, idx+1+x, n-1, results)


def solve():
    data = sys.stdin.read().split()
    n = int(data[0])
    read_cases(data, 1, n, [])


solve()
